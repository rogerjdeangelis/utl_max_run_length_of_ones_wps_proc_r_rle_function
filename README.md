# utl_max_run_length_of_ones_wps_proc_r_rle_function
Max run length of ones wps proc R rle function. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.


    Max run length of ones wps proc R rle function

    see github
    https://tinyurl.com/ycdvb6ax
    https://github.com/rogerjdeangelis/utl_max_run_length_of_ones_wps_proc_r_rle_function

    see stackoverflow
    https://tinyurl.com/ybjnefmb
    https://stackoverflow.com/questions/51266721/identifying-the-rows-with-maximum-continuous-values


    INPUT
    =====

    SD1.HAVE total obs=21
               |
    Obs    B   |
               |
      1    0   |
      2    0   |
      3    1   |
      4    1   |
      5    1   |
      6    0   |
      7    0   |
      8    0   |
      9    1   |
     10    0   |

     11    1   |  This is the logest run of 1s
     12    1   |  Run length is 6
     13    1   |
     14    1   |
     15    1   |
     16    1   |

     17    0   |
     18    0   |
     19    0   |
     20    1   |


    EXAMPLE OUTPUT
    --------------

    [1] "Max Run of 1s"
    [1] 6


    PROCESS  (Working WPS/Proc R code)
    ===================================

    runs <- rle(have$B);
    max(runs$lengths[runs$values==1]);


    OUTPUT
    ======

    [1] "Max Run of 1s"
    [1] 6


    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;


    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
    input B;
    datalines;
    0
    0
    1
    1
    1
    0
    0
    0
    1
    0
    1
    1
    1
    1
    1
    1
    0
    0
    0
    1
    0
    ;;;;
    run;quit;


    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;


    %utl_submit_wps64('
    libname sd1 "d:/sd1";
    options set=R_HOME "C:/Program Files/R/R-3.3.2";
    proc r;
    submit;
    source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T);
    library(haven);
    have<-read_sas("d:/sd1/have.sas7bdat");
    head(have);
    runs <- rle(have$B);
    "Max Run of 1s";
    max(runs$lengths[runs$values==1]);
    endsubmit;
    run;quit;
    ');


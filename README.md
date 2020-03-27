# utl-proc-report-greenbar-or-alternate-shading-of-rows-for-easy-reading
proc report greenbar or alternate shading of rows for easy reading
    proc report greenbar or alternate shading of rows for easy reading

    Algorithm by
         Andreas Grueninger <grueninger@IBGRUENINGER.DE>
         Tue, 19 Dec 2000 20:05:29 GMT  (SAS-L)

    Greenbar macro on end

    Output report with greenbars
    https://tinyurl.com/rramf2n
    https://github.com/rogerjdeangelis/utl-proc-report-greenbar-or-alternate-shading-of-rows-for-easy-reading/blob/master/greenbar.pdf

    github
    https://tinyurl.com/qvlh2hc
    https://github.com/rogerjdeangelis/utl-proc-report-greenbar-or-alternate-shading-of-rows-for-easy-reading

    related repo
    github
    https://tinyurl.com/yat3vzuz
    https://github.com/rogerjdeangelis/utl_proc_report_useful_tips_counters_conditional_rows_templates

    Stackoverflow
    https://tinyurl.com/vr7b783
    https://stackoverflow.com/questions/60877723/zebra-theme-in-sas-doesnt-with-with-noprint

    *_                   _
    (_)_ __  _ __  _   _| |_
    | | '_ \| '_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    ;

    SASHELP.CLASS

    SASHELP.CLASS total obs=19

    Obs    NAME       SEX    AGE    HEIGHT    WEIGHT

      1    Joyce       F      11     51.3       50.5
      2    Louise      F      12     56.3       77.0
      3    Alice       F      13     56.5       84.0
      4    James       M      12     57.3       83.0
      5    Thomas      M      11     57.5       85.0
      6    John        M      12     59.0       99.5
     .....

    *            _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| '_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    ;

     d:/pdf/greenbar.pdf

      Name       Sex    Age    Height    Weight

      Alfred      M      14     69.0      112.5
      Alice-------F------13-----56.5-------84.0  Highlighed with gray background
      Barbara     F      13     65.3       98.0
      Carol-------F------14-----62.8------102.5  Highlighed with gray background
      Henry       M      14     63.5      102.5
      James-------M------12-----57.3-------83.0  Highlighed with gray background
      Jane        F      12     59.8       84.5
      Janet-------F------15-----62.5------112.5  Highlighed with gray background
      Jeffrey     M      13     62.5       84.0

    *
     _ __  _ __ ___   ___ ___  ___ ___
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    ;

    ods pdf file="d:/pdf/greenbar.pdf" notoc;
    proc report nowd data=sashelp.class nowd missing;
      column name age sex height weight _row;
      %greenbar;
    run;quit;
    ods pdf close;

    *
     _ __ ___   __ _  ___ _ __ ___
    | '_ ` _ \ / _` |/ __| '__/ _ \
    | | | | | | (_| | (__| | | (_) |
    |_| |_| |_|\__,_|\___|_|  \___/

    ;

    %MACRO greenbar ;
       DEFINE _row / order COMPUTED NOPRINT ;
       COMPUTE _row;
          nobs+1;
          _row = nobs;
          IF (MOD( _row,2 )=0) THEN
             CALL DEFINE( _ROW_,'STYLE',"STYLE={BACKGROUND=graydd}" );
       ENDCOMP;
    %MEND greenbar;


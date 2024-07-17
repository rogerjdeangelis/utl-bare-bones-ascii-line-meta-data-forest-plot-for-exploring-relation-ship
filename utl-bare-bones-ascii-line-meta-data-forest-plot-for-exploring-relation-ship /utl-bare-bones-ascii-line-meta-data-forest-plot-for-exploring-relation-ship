%let pgm=utl-bare-bones-ascii-line-meta-data-forest-plot-for-exploring-relation-ships;

Bare bones forest plot for analyzing mutiple clinical trials

https://stackoverflow.com/questions/78746343/use-of-metaforest-for-plotting-data

  Two Solutions
      1 SAS proc plot (editied with cllassic 1980s editor)
      2 r forest plot

github
https://tinyurl.com/4fvuasbe
https://github.com/rogerjdeangelis/utl-bare-bones-ascii-line-meta-data-forest-plot-for-exploring-relation-ship

github
https://tinyurl.com/3w3h9dms
https://github.com/rogerjdeangelis/utl-bare-bones-ascii-line-meta-data-forest-plot-for-exploring-relation-ship/blob/main/forest.pdf

Related repos

https://github.com/rogerjdeangelis/utl-Meta-Analysis-of-Rare-Events
https://github.com/rogerjdeangelis/utl-meta-analysis-of-a-single-proportion-in-R-with-forest-and-funnel-plots
https://github.com/rogerjdeangelis/utl-meta-analysis-of-deaths-in-twenty-studies-with-forest-plot
https://github.com/rogerjdeangelis/utl-meta-analysis-of-a-single-proportion-in-R-with-forest-and-funnel-plots
https://github.com/rogerjdeangelis/utl-meta-analysis-of-deaths-in-twenty-studies-with-forest-plot
https://github.com/rogerjdeangelis/utl_meta_analysis_funnel_plot_odds_ratio_vs_standard_error
https://github.com/rogerjdeangelis/utl-meta-analysis-of-a-single-proportion-in-R-with-forest-and-funnel-plots
https://github.com/rogerjdeangelis/utl-meta-analysis-of-deaths-in-twenty-studies-with-forest-plot
https://github.com/rogerjdeangelis/utl-r-simple-random-forest-classification-example-using-iris-dataset
https://github.com/rogerjdeangelis/utl-random-forest-regression-vs-linear-regression-with-uncorrelated-independent-variables-in-r

/*               _     _
 _ __  _ __ ___ | |__ | | ___ _ __ ___
| `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
| |_) | | | (_) | |_) | |  __/ | | | | |
| .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
|_|
*/

/**************************************************************************************************************************/
/*                                                                                                                        */
/*   Create this plot                                                                                                     */
/*                                                                                                                        */
/*      -----------------------------------------------------------------------                                           */
/*      |           |                                                         |                                           */
/*      |           |   Risk Table                                            |                                           */
/*      |           |                                                         |                                           */
/*      |           |                     Risk   Lower  Upper                 |                                           */
/*      |           |            Study    Ratio   CI      CI                  |                                           */
/*      |                                                                     |                                           */
/*      |           E              A      2.7     1.7    4.3                  |                                           */
/*      |           Q              B      2.3     1.5    3.7                  |                                           */
/*      |           U              C      0.6     0.4    1.0                  |                                           */
/*      |           A              D      0.4     0.2    0.6                  |                                           */
/*      |           L              E      1.7     1.1    2.6                  |                                           */
/*      |                          F      3.8     2.3    6.3                  |                                           */
/*      |           R              G      6.1     3.4   11.3                  |                                           */
/*      |           I              H      1.9     1.2    2.9                  |                                           */
/*      |           S              I      0.3     0.2    0.5                  |                                           */
/*      |           K                                                         |                                           */
/*      |           |                Risk Ratio                               |                                           */
/*      --+----+----+----+----+----+----+----+----+----+----+----+----+----+---                                           */
/*      |      0    1    2    3    4    5    6    7    8    9   10   11   12  |                                           */
/*      |           |                                                         |                                           */
/*      |           | Confidence interval not centered (logistic intervals?)  |                                           */
/*      |           |                                                         |                                           */
/*      |       0.3 |                                                         |                                           */
/*    I +       [*-]|                                                         + I                                         */
/*      |           |  1.9                                                    |                                           */
/*    H +           |[--*----]                                                + H                                         */
/*      |           |                        6.1                              |                                           */
/*    G +           |           [-------------*------------------------]      + G                                         */
/*      |           |            3.8                                          |                                           */
/*    F +           |     [-------*-----------]                               + F                                         */
/*      |           |  1.7                                                    |                                           */
/*    E +           |[--*---]                                                 + E                                         */
/*      |       0.4 |                                                         |                                           */
/*    D +       [*] |                                                         + D                                         */
/*      |           |                                                         |                                           */
/*    C +    0.6 [*-]                                                         + C                                         */
/*      |           |     2.3                                                 |                                           */
/*    B +           | [----*-----]                                            + B                                         */
/*      |           |      2.7                                                |                                           */
/*    A +           |   [----*-------]                                        + A                                         */
/*      |           |                                                         |                                           */
/*      --+----+----+----+----+----+----+----+----+----+----+----+----+----+---                                           */
/*             0    1    2    3    4    5    6    7    8    9   10   11   12                                              */
/*                                    Risk Ratio                                                                          */
/*                                                                                                                        */
/**************************************************************************************************************************/

/*                   _                   _                 _               _
/ |  ___  __ _ ___  (_)_ __  _ __  _   _| |_    ___  _   _| |_ _ __  _   _| |_
| | / __|/ _` / __| | | `_ \| `_ \| | | | __|  / _ \| | | | __| `_ \| | | | __|
| | \__ \ (_| \__ \ | | | | | |_) | |_| | |_  | (_) | |_| | |_| |_) | |_| | |_
|_| |___/\__,_|___/ |_|_| |_| .__/ \__,_|\__|  \___/ \__,_|\__| .__/ \__,_|\__|
                            |_|                               |_|
*/

libname sd1 "d:/sd1";
options validvarname=upcase;
data sd1.have ;;
input study_ID$ risk_ratio lb_conf_int ub_conf_int;
*format risk_ratio lb_conf_int ub_conf_int 5.1;
cards4;
A 2.70 1.71 4.31
B 2.33 1.49 3.66
C 0.64 0.42 0.97
D 0.37 0.23 0.59
E 1.70 1.11 2.61
F 3.76 2.28 6.27
G 6.14 3.40 11.28
H 1.86 1.21 2.86
I 0.30 0.18 0.49
;;;;
run;quit;

proc print data=sd1.have;
run;quit;

options ls=80 ps=37;
proc plot data=sd1.have;
  plot
        study_id*lb_conf_int='['
        study_id*risk_ratio='*'
        study_id*ub_conf_int=']'
           / overlay box href=1
  haxis = -1 to 12;
run;quit;

/**************************************************************************************************************************/
/*                                                                                                                        */
/*                                                                                                                        */
/*     --+----+----+----+----+----+----+----+----+----+----+----+----+----+---                                            */
/* _ID |           |                                                         |                                            */
/*   I +       [*  |                                                         +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   H +           |[  *    ]                                                +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   G +           |           [             *                        ]      +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   F +           |     [       *           ]                               +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   E +           |[  *   ]                                                 +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   D +       [*] |                                                         +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   C +        [* ]                                                         +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   B +           | [    *     ]                                            +                                            */
/*     |           |                                                         |                                            */
/*     |           |                                                         |                                            */
/*   A +           |   [    *       ]                                        +                                            */
/*     --+----+----+----+----+----+----+----+----+----+----+----+----+----+---                                            */
/*     -1.0  0.0  1.0  2.0  3.0  4.0  5.0  6.0  7.0  8.0  9.0 10.0 11.0 12.0                                              */
/*                                                                                                                        */
/*                                   LB_CONF_INT                                                                          */
/*                                                                                                                        */
/*                                                                                                                        */
/*               RISK_    LB_CONF_    UB_CONF_                                                                            */
/*   STUDY_ID    RATIO       INT         INT                                                                              */
/*                                                                                                                        */
/*      A         2.70      1.71         4.31                                                                             */
/*      B         2.33      1.49         3.66                                                                             */
/*      C         0.64      0.42         0.97                                                                             */
/*      D         0.37      0.23         0.59                                                                             */
/*      E         1.70      1.11         2.61                                                                             */
/*      F         3.76      2.28         6.27                                                                             */
/*      G         6.14      3.40        11.28                                                                             */
/*      H         1.86      1.21         2.86                                                                             */
/*      I         0.30      0.18         0.49                                                                             */
/*                                                                                                                        */
/**************************************************************************************************************************/


/*___                             _       _
|___ \   _ __    __ _  __ _ _ __ | | ___ | |_
  __) | | `__|  / _` |/ _` | `_ \| |/ _ \| __|
 / __/  | |    | (_| | (_| | |_) | | (_) | |_
|_____| |_|     \__, |\__, | .__/|_|\___/ \__|
                |___/ |___/|_|
*/

%utl_rbeginx;
parmcards4;
library(ggplot2)
library(haven)
data<-read_sas("d:/sd1/have.sas7bdat")
data
pdf(file="d:/pdf/forest.pdf",height=8,width=10);
ggplot(data, aes(RISK_RATIO, STUDY_ID)) +
  geom_segment(aes(x = LB_CONF_INT, xend = UB_CONF_INT)) +
  geom_point(shape = 15, color = "gray50", size = 6) +
  theme_classic(16) +
  labs(x = "Risk ratio", y = "Study ID") +
  geom_vline(xintercept = 1, linetype = 2)
pdf()
;;;;
%utl_rendx;

/*              _
  ___ _ __   __| |
 / _ \ `_ \ / _` |
|  __/ | | | (_| |
 \___|_| |_|\__,_|

*/

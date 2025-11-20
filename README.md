README
================
Yinuo Zhou
2025-11-20

## R Package: Counting Missing Data

#### Introduction

This repository is for my assignment of STAT 545B in UBC. Using the
prebake file provided by my instructors, I created an R package
“CountingMissingData” that contains a function that allows the users
count the missing values for all columns by groups.

\####Installation You can install the development version of
CountMissingData from GitHub with:

``` r
# install.packages("pak")
pak::pak("stat545ubc-2025/CountMissingData")
```

    ## ✔ Updated metadata database: 5.91 MB in 15 files.
    ## ℹ Updating metadata database✔ Updating metadata database ... done
    ##  
    ## → Will install 15 packages.
    ## → Will update 1 package.
    ## → Will download 15 CRAN packages (8.70 MB).
    ## → Will download 1 package with unknown size.
    ## + cli                           3.6.5      [dl] (1.40 MB)
    ## + CountMissingData 0.0.0.9000 → 0.0.0.9000 [bld][cmp][dl] (GitHub: f1f0cf1)
    ## + dplyr                         1.1.4      [dl] (1.58 MB)
    ## + generics                      0.1.4      [dl] (84.66 kB)
    ## + glue                          1.8.0      [dl] (183.69 kB)
    ## + lifecycle                     1.0.4      [dl] (141.02 kB)
    ## + magrittr                      2.0.4      [dl] (229.05 kB)
    ## + pillar                        1.11.1     [dl] (673.34 kB)
    ## + pkgconfig                     2.0.3      [dl] (22.81 kB)
    ## + R6                            2.6.1      [dl] (88.59 kB)
    ## + rlang                         1.1.6      [dl] (1.63 MB)
    ## + tibble                        3.3.0      [dl] (698.31 kB)
    ## + tidyselect                    1.2.1      [dl] (227.98 kB)
    ## + utf8                          1.2.6      [dl] (155.23 kB)
    ## + vctrs                         0.6.5      [dl] (1.36 MB)
    ## + withr                         3.0.2      [dl] (231.63 kB)
    ## ℹ Getting 15 pkgs (8.70 MB) and 1 pkg with unknown size
    ## ✔ Got CountMissingData 0.0.0.9000 (source) (6.54 kB)
    ## ✔ Got lifecycle 1.0.4 (i386+x86_64-w64-mingw32) (141.71 kB)
    ## ✔ Got R6 2.6.1 (i386+x86_64-w64-mingw32) (88.75 kB)
    ## ✔ Got cli 3.6.5 (x86_64-w64-mingw32) (1.40 MB)
    ## ✔ Got generics 0.1.4 (i386+x86_64-w64-mingw32) (85.04 kB)
    ## ✔ Got glue 1.8.0 (x86_64-w64-mingw32) (184.23 kB)
    ## ✔ Got dplyr 1.1.4 (x86_64-w64-mingw32) (1.59 MB)
    ## ✔ Got pkgconfig 2.0.3 (i386+x86_64-w64-mingw32) (23.01 kB)
    ## ✔ Got tidyselect 1.2.1 (i386+x86_64-w64-mingw32) (229.03 kB)
    ## ✔ Got magrittr 2.0.4 (x86_64-w64-mingw32) (228.89 kB)
    ## ✔ Got rlang 1.1.6 (x86_64-w64-mingw32) (1.63 MB)
    ## ✔ Got pillar 1.11.1 (i386+x86_64-w64-mingw32) (673.57 kB)
    ## ✔ Got withr 3.0.2 (i386+x86_64-w64-mingw32) (232.98 kB)
    ## ✔ Got tibble 3.3.0 (x86_64-w64-mingw32) (698.24 kB)
    ## ✔ Got utf8 1.2.6 (x86_64-w64-mingw32) (155.23 kB)
    ## ✔ Got vctrs 0.6.5 (x86_64-w64-mingw32) (1.37 MB)
    ## ✔ Installed R6 2.6.1  (452ms)
    ## ✔ Installed generics 0.1.4  (726ms)
    ## ✔ Installed pkgconfig 2.0.3  (1s)
    ## ✔ Installed utf8 1.2.6  (1.1s)
    ## ✔ Installed magrittr 2.0.4  (1.4s)
    ## ✔ Installed rlang 1.1.6  (1.5s)
    ## ✔ Installed lifecycle 1.0.4  (1.6s)
    ## ✔ Installed tidyselect 1.2.1  (1.7s)
    ## ✔ Installed withr 3.0.2  (1.7s)
    ## ✔ Installed glue 1.8.0  (2s)
    ## ✔ Installed cli 3.6.5  (2.1s)
    ## ✔ Installed vctrs 0.6.5  (2.1s)
    ## ✔ Installed dplyr 1.1.4  (2.3s)
    ## ✔ Installed pillar 1.11.1  (2.4s)
    ## ✔ Installed tibble 3.3.0  (2.5s)
    ## ℹ Packaging CountMissingData 0.0.0.9000
    ## ✔ Packaged CountMissingData 0.0.0.9000 (1s)
    ## ℹ Building CountMissingData 0.0.0.9000
    ## ✔ Built CountMissingData 0.0.0.9000 (1.5s)
    ## ✔ Installed CountMissingData 0.0.0.9000 (github::stat545ubc-2025/CountMissingData@f1f0cf1) (228ms)
    ## ✔ 1 pkg + 15 deps: upd 1, added 15, dld 16 (NA B) [28.4s]

\####Example This is a simple example to demonstrate how you can use
this package: This example computes the number of missing values in the
`airquality` dataset grouped by the `cyl` column.

``` r
library(CountMissingData)
library(tidyverse)
```

    ## Warning: package 'tibble' was built under R version 4.5.2

    ## Warning: package 'readr' was built under R version 4.5.2

    ## Warning: package 'dplyr' was built under R version 4.5.2

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.2
    ## ✔ ggplot2   4.0.0     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.1.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
count_all_missing_by_group(airquality, Month)
```

    ## # A tibble: 5 × 6
    ##   Month Ozone Solar.R  Wind  Temp   Day
    ##   <int> <int>   <int> <int> <int> <int>
    ## 1     5     5       4     0     0     0
    ## 2     6    21       0     0     0     0
    ## 3     7     5       0     0     0     0
    ## 4     8     5       3     0     0     0
    ## 5     9     1       0     0     0     0

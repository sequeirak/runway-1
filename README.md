
<!-- README.md is generated from README.Rmd. Please edit that file -->

# runway

<!-- badges: start -->

[![Lifecycle:
maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
<!-- badges: end -->

The goal of runway is to generate statistics and plots to calculate
discrimination, calibration, and decision curves for prediction models.

## Installation

You can install `runway` from GitHub with:

``` r
remotes::install_github('ML4LHS/runway')
```

## Load the package

First, load the package.

``` r
library(runway)
```

## Sample datasets

Runway comes with two sample datasets.

``` r
data(single_model_dataset)
head(single_model_dataset)
#>   outcomes predictions
#> 1        0        0.36
#> 2        1        0.31
#> 3        0        0.39
#> 4        0        0.09
#> 5        0        0.44
#> 6        1        0.22

data(multi_model_dataset)
head(multi_model_dataset)
#>   outcomes predictions model_name
#> 1        0        0.26    Model 2
#> 2        1        0.28    Model 1
#> 3        0        0.56    Model 2
#> 4        0        0.27    Model 1
#> 5        0        0.31    Model 1
#> 6        0        0.42    Model 2
```

## Threshold-performance plot (single model)

``` r
threshperf_plot(single_model_dataset,
                outcome = 'outcomes',
                prediction = 'predictions')
```

<img src="man/figures/README-unnamed-chunk-5-1.png" width="100%" />

## Threshold-performance plot (multiple models)

``` r
threshperf_plot_multi(multi_model_dataset,
                      outcome = 'outcomes',
                      prediction = 'predictions',
                      model = 'model_name')
```

<img src="man/figures/README-unnamed-chunk-6-1.png" width="100%" />

## Calibration plot (single model)

``` r
cal_plot(single_model_dataset,
         outcome = 'outcomes', 
         prediction = 'predictions',
         n_bins = 5)
#> Warning: Removed 2 rows containing missing values (geom_bar).
```

<img src="man/figures/README-unnamed-chunk-7-1.png" width="100%" />

## Calibration plot (multiple models)

``` r
cal_plot_multi(multi_model_dataset,
         outcome = 'outcomes',
         prediction = 'predictions',
         model = 'model_name',
         n_bins = 5)
```

<img src="man/figures/README-unnamed-chunk-8-1.png" width="100%" />
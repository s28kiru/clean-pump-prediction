# CLEAN PUMP PREDICTION

- Part of `Data for good` initiative
- Using data from `Taarifa` to predict which pumps work well, needs repair and do not work at all
- Competition hosted by `Driven Data`
- Link: https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/

## Data dictionary and initial analysis

##### 1. - `id` - unique entry - no NA - good with train and test
##### 2. - `amount_tsh` - Total static head (amount water available to waterpoint)-  possible outliers (in both train and test)
#### 3. `date_recorded` - The date the row was entered
#### 4. `funder` - Who funded the well - contains na
##### 5. - `gps_height` - Altitude of the well - no outliers - not normal either - 0 - 500 a lot
##### 6. - `installer` - Organization that installed the well - contains na
##### 7. - `longitude` 
##### 8. - `latitude` 
##### 9. - `wpt_name` - Name of the waterpoint if there is one
##### 10. - `num_private` - possible outliers
##### 11. - `basin` - Geographic water basin - 9 unique
##### 12. - `subvillage` - Geographic location - combine and bin maybe
##### 13. - `region` - Geographic location - 21 unique
##### 14. - `region_code` - Geographic location (coded) - 27 unique 
##### 15. - `district_code` - Geographic location (coded)
##### 16. - `lga` - Geographic location
##### 17. - `ward` - Geographic location
##### 18. - `population` - Population around the well - possible outliers
##### 19. - `public_meeting` - True/False - contains NA
##### 20. - `recorded_by` - Group entering this row of data - nvz
##### 21. - `scheme_management` - Who operates the waterpoint - contains na - 12 unique
##### 22. - `scheme_name` - Who operates the waterpoint - contains NA - lot of unique - can be binned
##### 23. - `permit` - If the waterpoint is permitted - contains NA - can be imputed with majority class (TRUE)
##### 24. - `construction_year` - Year the waterpoint was constructed - contains junk - 0 - 55 unique values (54 years and 1 junk 0)
##### 25. - `extraction_type` - The kind of extraction the waterpoint uses - 18 unique values - `gravity` is majority class - can be binned as `gravity` and other 
##### 26. - `extraction_type_group` - The kind of extraction the waterpoint uses - 13 unique values
##### 27. - `extraction_type_class` - The kind of extraction the waterpoint uses - 7 unique values - possible correlation between variable number 25, 26 and 27
##### 28. - `management` - How the waterpoint is managed - `vwc` more than 70% values - possible nvz
##### 29. - `management_group` - How the waterpoint is managed - `user_group` majority more than 80% - possible nvz
##### 30. - `payment` - What the water costs - 7 unique values - 50% `never_pay`
##### 31. - `payment_type` - What the water costs - 7 unique values - possible aliased variable with variable 30
##### 32. - `water_quality` - The quality of the water - 8 unique values - 95% values `soft` - possible nvz
##### 33. - `quality_group` - The quality of the water - 6 unique values - 95% values   `good` - possible nvz
##### 34. - `quantity` - The quantity of water - 5 unique values including `unknown` - more than 50% `enough`
##### 35. - `quantity_group` - The quantity of water - 5 unique - confirm aliased variable of variable 34
##### 36. - `source` - The source of the water - 10 unique values
##### 37. - `source_type` - The source of the water - variable 36 - binned - 7 unique values
##### 38. - `source_class` - The source of the water - variable 37 binned - 3 unique values
##### 39. - `waterpoint_type` - The kind of waterpoint - 7 unique values - `communal_standpipe` more than 50%, `hand pump` 2nd majority class
##### 40. - `waterpoint_type_group` - The kind of waterpoint - 6 unique values - variable 39 binned `communal_standpipe` as 1 type


#### Numerical features

amount_tsh, gps_height, 

#### Categorical features

#### Spatial features

longitude, latitude, subvillage, region, region_code, district_code, lga, ward

#### Temporal features

date_recorded

## Modelling

#### Baseline model - columns

###### Same as it is - amount_tsh, gps_height, num_private, population
###### dummy - status_group, basin, region, district_code, extraction_type_group, payment, source, waterpoint_type
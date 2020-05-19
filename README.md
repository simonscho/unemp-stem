# unemp-stem
  
a data visualization that explores the connection between US unemployment rates and the proportion of STEM degrees awarded by the University of Michigan system (Ann Arbor, Dearborn, and Flint) between the years 2004 and 2016

#### raw data used

1. yearly labor force data from the [US Bureau of Labor Statistics](https://www.bls.gov/cps/tables.htm)
2. yearly degree reports (by field of specialization) from the [University of Michigan](https://ro.umich.edu/reports/degrees)
3. list of DHS designated STEM fields, as found on the [NAFSA website](https://www.nafsa.org/professional-resources/browse-by-interest/dhs-stem-designated-degree-program-list-2012)

#### how data was processed

1. yearly labor force data from US BLS
   - converted from xlsx to csv via pandas
2. yearly degree reports from UofM
   - converted from xls(x) to csv via pandas
   - each type of degree marked as either STEM or not STEM, depending on whether the degree name contains a STEM keyword (see 3. below)
   - aggregated over STEM/not STEM to get % STEM among total
3. list of STEM fields
   - cleaned website source code, took first word of each entry to get list of STEM keywords

#### results of processed data

1. cpsa2019.csv
2. 2004.csv - 2016.csv (2007 and 2008 data missing, see 'caveats' below)
3. stemkeywords.txt

#### caveats

- the data for 2007 and 2008 degrees from UofM are missing. this is because UofM has chosen to format the data for those specific years in .pdf instead of .xls(x) or .csv. so instead of spending time dealing with this, i decided to omit the 2007 and 2008 data, since (1) the plot doesn't hide the fact that this data is missing and (2) i'm secretly mainly interested in the effect of the 2008 economic recession and its necessarily delayed effect on the proportion of STEM degrees.
- the method used to mark degrees as STEM/not STEM is rough (taking the first word of the list of STEM degrees, and matching each degree against this list), and so might have resulted in a few false positives/negatives. on balance this doesn't matter much, since each individual degree type accounts for a small portion of the total number of degrees, and i don't expect that many errors even with the rough method used (the reader is invited to check stemkeywords.txt for the list of STEM keywords used).

#### conclusions/observations

there is a sharp increase in unemployment beginning between 2007 and 2008, and a sharp increase in proportion of STEM degrees beginning between 2011 and 2012
- this aligns with the naive expectation that panic about the economy would take about four years (the usual length of college) to translate into an increase in the proportion of STEM degrees. less naively, one might expect the delay to have been shorter, since undergraduate students typically have until their sophomore year to declare their majors. perhaps this was counterbalanced by natural inertia in making big changes in response to new phenomena, and the fact that the students will have already taken classes towards their expected (but not necessarily declared) major by the end of their freshman year.
- note that while unemployment came back down relatively soon, the increase in % of STEM degrees is sustained. this might be due to several factors, including (1) the delay in economic reality filtering through to popular perception and (2) the ascendancy of STEM topics (such as AI and data science) in popular consciousness

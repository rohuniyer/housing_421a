# housing_421a
(Re-adding code and maps from old repo)


## Background
The Housing 421A repository contains scripts to gather, analyze and map data related to the 421-a tax abatement program in New York City. There are multiple efforts to replace the program, with a larger focus on consistently providing affordable units for New Yorkers, something the current program has failed at. The data generated here is in support of efforts to highlight many of the 421-a shortcomings. 


## Data

I use a number of data sources here from various places. I have provided links to them below:
- 421A Properties NYC: https://www1.nyc.gov/site/finance/benefits/benefits-421a.page 
    - Files saved as: 421a_2021_queens.xlsx
    - This page provided by the NYC Dept of Finance has current and historical 421a properties by borough. For all analysis done here, this is the ground truth on 421a properties in NYC. 
- NY State Assembly Districts: https://www1.nyc.gov/site/planning/data-maps/open-data/districts-download-metadata.page 
    - Files saved as: nyad.csv
    - This is the official maps/shapefiles for all NY state district boundaries (Assembly Districts, State Senate, US Congressional)


## Analyses

I'll update this. But for now, you can read about the analysis here: https://www.rohuniyer.com/421a-analysis.html 


## Notebooks

### createTaxClassFiles.ipynb
This notebook identifies 421a buildings by Assembly District (AD), creates tables for each tax class and saves the building data to separate CSVs. This project started by working with AD36 so the file is geared towards that but can be easily switched to any other NYC AD. 

I use the 421A Properties file, NYC Open Data building locations and NY State Assembly District boundaries. 

### scrape_propertyTax.ipynb

This notebook takes the newly created tax class files and uses them to access the property tax forms for each 421A building for 2019, 2020, and 2021. For each building, we are looking for the number of reported rent-regulated units. 

As all the property tax documents are in PDF format, the process includes downloading a given PDF, finding the relevant section with reported rent-regulated units, "scraping" those values and putting them into another CSV. I also create a pivot table for simpler tracking of properties and their reported units over time. 

This process is a bit cumbersome and requires finding the actual area of the PDF where this information is located. As of March 2022, this only includes Tax Classes 2 and 2B as they are the only classes with relatively standard tax documents. (Also why I have only focused on 2019-2021 since previous years have a different format.)

### abatement_values.ipynb

Using NYC Open Data, this file adds actual tax abatement amounts for 421A properties. The API provided only gives values for 2018/19 so it's not a perfect match for a lot of the information above. However, I feel it provides important context to the 421A issue. 



## Further Reading/Analysis
For more reading on 421-a and outputs from thsi repo check out the following:
- Inconsistent tax reportings: https://www.rohuniyer.com/421a-analysis.html 
- A Better Way Than 421-a from NYC Comptroller Brad Lander's office: https://comptroller.nyc.gov/reports/a-better-way-than-421a/ 





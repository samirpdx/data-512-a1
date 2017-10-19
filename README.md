# A1. Data Curation

### Goal of the Project:

The goal of this project is to reproduce an analysis of traffic on English Wikipedia over time. I have documented the process in this Jupyter notebook starting with API pulls to obtain the raw data, followed by a series of data processing steps, and ultimately a data visualization of the Wikipedia traffic.

### License of the Source Data

Data was gathered from the Wikimedia REST API, Wikimedia Foundation, 2017. CC-BY-SA 3.0

<a href = "https://wikimediafoundation.org/wiki/Terms_of_Use/en"> WikiMedia Terms of Use</a>

### Links to Relevant API Documentation

To collect data for Wikipedia traffic from 2008-2016, two different API endpoints, the Pagecounts API and the Pageviews API, were used.

Pagecounts API (older, legacy metric) provides access to desktop and mobile traffic data for the period of January 2008 through July 2016.

[documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts)

<a href = "https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end">endpoint </a>

The Pageviews API (a newer metric) provides access to desktop, mobile web, and mobile app traffic data for the period of July 2015 through September 2017.

[documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews")

[endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)

This data is made available via CC0 1.0 license.


### Data set fields (final CSV output)

Below are the columns in order found in the 'n-wikipedia_traffic_200801-201709.csv' file:

##### Listed as: Column Name (Data Type)

year (int)

month (int)

pagecount_allviews (int)

pagecount_desktopviews (int)

pagecount_allviews (int)

pagecount_allviews (int)

pagecount_allviews (int)

pagecount_allviews (int)



### Special considerations and Known Issues

- API Data sourced from the PageView endpoint excludes spiders/crawlers with arguments for "agent".  However, the older metric of PageCounts does not exclude this and thus results in overcounting.  As a result, the API call for PageCount does not require the argument "agent".

- CSV output file will contain rows with zero values (representing months where there is no data).  This will need to be ignored to reproduce identical plot.

- The PageViews data is split into mobile-app and mobile-web categories, which would later need to be combined into one sum of views for mobile data.

- Mobile and Desktop data were combined for "all views" columns in the final CSV for the PageViews and PageCounts respectively.

- In the parameters used for API calls, there are key/value differences.  Page Counts uses ‘access-site’ and 'as an argument. Page Views uses ‘access’

- For view totals, PageCounts uses "count" as its argument for storing views whereas PageViews uses "views".

- In order to create a time series plot, the month and year columns need to be converted to datetime format. One recommendation is creating a new data object for this datetime format.

Directory Structure
---------------------
```
data-512-a1/

  |- final_data/
     |- en-wikipedia_traffic_200801-201709.csv
  |- images/
     |- pageviews_english_wikipedia.png
  |- raw_data/
     |- pagecounts_desktop-site_200801-201607
     |- pagecounts_mobile-site_200801-201607
     |- pageviews_desktop_201507-201709
     |- pageviews_mobile-app_201507-201709
     |- pageviews_mobile-web_201507-201709
  |- LICENSE     
  |- README.md
  |- hcds-a1-data-curation.ipynb
```

### Reproducibility Steps

Please reference the Jupyter Notebook,'hcds-a1-data-curation.ipynb', to see step by step instructions of how to perform the analysis.

Steps are broken out as follows:

    Step 1: Data Acquisition (API Requests)
    
    Step 2: Data Processing
    
    Step 3: Analysis
    

### Attributions

Jonathan Morgan (Professor, DATA 512, Human Centered Data Science, University of Washington) for example source code provided for API data requests.
    - Specific attributes found in 'hcds-a1-data-curation.ipynb'

Additional instructions provided by [HCDS Fall 2017 - Course Wiki](https://wiki.communitydata.cc/HCDS_(Fall_2017)/Assignments#Weekly_reading_reflections).  CC-BY-SA 3.0
English Wikipedia page views 2007 - 2018
2018-10-17
Authored by Paul Wright

We use the public API system from Wikipedia to gather and graph page views on their site. This goal is broken up into the following 3 sections which are covered in more detail below:

1) Gathering the data
2) Processing the data
3) Graphing the data

Section 1: Gathering the data

We leverage the 2 available APIs (one legacy, one current) to gather page view data across mobile and desktop devices. For the legacy system, this involves making 2 API calls (1 per device type). For the new system, this requires 3 API calls (once for deskop, once for mobile web and once for mobile app. In the new system, we also filter out 'agent=user' to eliminate crawlers or automated traffic. Each of the 5 results are stored (in their raw form) in the data folder.

Section 2: Processing the data

After all the data has been gathered, we manipulate the data to obtain the following table:

year
month
pagecount_all_views
pagecount_desktop_views
pagecount_mobile_views
pageview_all_views
pageview_desktop_views
pageview_mobile_views

This requires merging the five datasets on the year and month, merging mobile-app and mobile-web on the pageviews to obtain mobile, breaking out the month and year separately, and saving to 'en-wikipedia_traffic_200801-201709.csv'

Section 3: Graphing the data

Using the data from section 2, we plot the trends. First, we convert the year and month into pandas datetime so plotting is consistent. Once the plot is generated, we display inline and save a version as a png for reference.




Source data:

https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions
API is licensed under the CC-BY-SA 3.0 and GFDL licenses

Pageviews:

API: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews
endpoint: https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end

Pagecounts:

API:https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts
endpoint: https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end
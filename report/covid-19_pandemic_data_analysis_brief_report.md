# COVID-19 Pandemic Data Analysis

------------------------------------------------------------------------

*Links to SQL commands and visualization*

-   [Queries: to clean data](https://console.cloud.google.com/bigquery?sq=72277525562:9e6808cd080b4bbe9f2d0b7c11766ddc)
-   [Queries: to explore and organize data](https://console.cloud.google.com/bigquery?sq=72277525562:8d48deb7d0a94c26bc814e435bd9b27b)
-   [COVID19_Dashboard](https://public.tableau.com/views/Project_01_16774494951790/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link)

------------------------------------------------------------------------

When we turn around and have a look on the past, we can understand that over time, the world has travelled through many pandemics and epidemics. Some of these outbreaks have wiped out a large population of the world. Today's modern world is no exception to these rapidly spreading severe diseases.

The latest to join the list of global pandemics is the Corona Virus Disease, commonly called as the COVID-19. It is a contagious disease caused by a virus, the Severe Acute Respiratory Syndrome Corona Virus 2 (SARS-CoV-2). In December 2019, we had the first case of this disease in Wuhan, China. The disease quickly spread worldwide, resulting in the pandemic.

The significant factor of today's world is the advancement of science and technology. It has played a great role from tracking and diagnosing the disease to producing the vaccines. In this analysis project, we will study the impact of the disease, the efficiency of vaccines and many factors using the data that is available.

## Data Collection

Many factors should be considered during the data collection process, such as:

-   How the data will be collected?
-   Choose data sources.
-   Decide what data to use.
-   How much data to collect.
-   Select the right data type.
-   Determine the time frame.

In this analysis, the source of the data is significant because there are many platforms that offer data related to this topic.

The data are collected from the following sources:

-   World Health Organization (WHO) -- It is a specialized agency of the United Nations responsible for international public health. [WHO Covid19 Data](https://covid19.who.int/data).
-   Our World in Data -- It is a project of the Global Change Data Lab, a non-profit organization based in the United Kingdom. It focuses on increasing the use of data and evidence to make progress against the world's largest problems.[Our World in Data: Covid19](https://ourworldindata.org/covid-deaths).

Both the data sources can be classified as secondary, structured and quantitative data. They are gathered by other people or from another research. They are specific and objective measures of numerical facts and are organized in a certain format.

## Data Preparation

Before using the data for analysis, it is important to clean it. A dirty data could lead to many issues during the analysis process.

As the dataset contains many observations, BigQuery has been used to view and transform the data.

The data exploration stage has helped to identify some potential areas that needed to be cleaned:

-   Incorrect data types: The raw dataset contained of attributes with incorrect data types. These types are changed using the CAST() function.
-   Many attributes within a single table which complicated the viewability: The raw dataset has the entire collection of information including number of cases, deaths and vaccinations. For making the analysis process simple, the raw dataset has been split into two different tables:
    -   covid_cases -- contains attributes related to cases and deaths.
    -   covid_vaccines -- contains attributes related to vaccinations.
-   Unnecessary "NULL" values: These values are converted to zero using the IFNULL() function.
-   Data repetition: Country and Continent-based observations clubbed together. The covid_cases and covid_vaccines table consists only Country-based observations.
    -   This was done by adding the WHERE clause: continent IS NOT null.
-   All vaccine types under one attribute: The comma-separated vaccines types were separated into individual columns using "Text-to-columns" option. To indicate if a country has used a specific vaccine type, IF() function has been used. Example: =IF(A2 = "<vaccine type>";1;0) ![Vaccine type usage indication](E:/GitHub/covid19-pandemic-data-analysis/report/screenshots/if_function_vaccine_types.png)

Definition of each attribute in the tables can be found here:

-   [WHO Covid19 Data - Attribute details](https://covid19.who.int/data/)
-   [Our World in Data: Covid19 - Attribute details](https://github.com/owid/covid-19-data/tree/master/public/data/)

The dataset contains information from 01-01-2020 to 20-02-2023.

## Analysis and Visualization

The following tables are created from the raw dataset:

-   covid_all_data
-   covid_cases
-   covid_data_continents
-   covid_vaccines

Using them, many relationships and patterns are found, and calculations are performed. Some of them are:

-   day-wise total death percent calculation
-   day-wise new cases percent calculation
-   countries with highest total cases
-   total deaths and cases in all countries
-   continent-wise total deaths
-   total cases, total deaths, total population, percentage of total deaths
-   vaccination and population comparison

Though the results show the patterns regarding the outbreak of corona and the measures taken to control them, more understandable conclusions can be drawn when the analyzed data is visualized.

Hence, the tables are imported to a data visualization tool, called Tableau. Visuals are created to study the following:

-   Worldwide cases and deaths
-   Continent-wise total deaths
-   Country-wise comparison of total cases
-   Change in new cases over time (Country-wise)
-   Vaccinations in all countries and types of vaccines used

The individual visuals are combined in an interactive dashboard.

Here are some of the findings from the visualized data:

The world population being 7.9 billion, around 672 million people are affected by corona. Out of this, around 6.8 million people have died, which is around 1.02 % of the population affected.

Europe has the highest number of deaths with over 2 million, followed by Asia around 1.6 million, North America around 1.5 million, South America around 1.3 million, Africa around 0.2 million and Oceania around 24 thousand.

From the comparison map, we can identify the total cases among all the countries, and it shows that the United States have recorded the most number of cases over the last three years. With a population of over 300 million, the total number of cases is more than 100 million and around 1 million people have died. From this map, the total number of cases in all countries can be found and can be compared with other countries using the filter options.

The bubble plot in the dashboard shows the total vaccinations (first and second dose) in each country.

The line graph in the bottom displays the increase and decrease of cases in each country over time. Most of the countries including United States, France, India, Italy, and Argentina have experienced a peak in the daily recorded cases between November 2021 and May 2022.

The pandemic started during the end of 2019 and within a year the scientists have managed to develop vaccines to control the spreading of the disease. In July 2020, China started to provide vaccines for its people. After that many countries started their vaccination campaigns by the end of 2020. Approximately there are around 40 types of vaccines. Some of the popular companies that formulated the vaccines are:

-   Moderna
-   Pfizer - BioNTech
-   Johnson & Johnson
-   AstraZeneca, etc.

More than 160 countries in the world have used the vaccine called Pfizer BioNTech -- Comirnaty and many countries have used more than one vaccine type.

From the visualization (dashboard) we can get a better understanding of the pandemic outbreak, measures taken and implemented to control the disease.

------------------------------------------------------------------------

*References*

1.  [Google Data Analytics](https://www.coursera.org/professional-certificates/google-data-analytics)
2.  [Youtube videos 01](https://www.youtube.com/@AlexTheAnalyst)
3.  [Youtube videos 02](https://www.youtube.com/@LukeBarousse)

------------------------------------------------------------------------

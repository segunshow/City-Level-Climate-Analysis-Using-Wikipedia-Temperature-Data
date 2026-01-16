# City-Level-Climate-Analysis-Using-Wikipedia-Temperature-Data

## Overview

This project provides a comprehensive analysis of city-level temperature variability, stability, and extremes across the globe. The focus is on moving beyond misleading national averages to produce actionable climate intelligence for urban planning, energy management, agriculture, and tourism.

The dataset was scraped from Wikipedia: List of Cities by Average Temperature
. Analysis was performed using Power BI, with custom DAX measures to quantify climate stability, volatility, and city rankings.

## Project Objectives

Analyze monthly and yearly temperature patterns across cities worldwide.

Identify extreme climate exposure points (hottest, coldest, most stable, most volatile cities).

Quantify temperature volatility using monthly temperature range and standard deviation.

Classify cities into Climate Stability Categories for actionable insights.

Enable dynamic exploration using Power BI dashboards.

## Dataset

Source: Wikipedia – List of Cities by Average Temperature

Granularity: Monthly average temperatures for 12 months

Geography: Cities from all inhabited continents

Variables:

Independent: Country, City, Month

Dependent: Monthly Average Temperature, Yearly Average Temperature

## Industry & Applications

Industry Type: Climate & Weather Analytics 🌦️

Related Sectors:

Urban Planning & Infrastructure

Environmental Research & Climate Change

Agriculture & Food Security

Tourism & Hospitality

Energy & Utilities

Primary Stakeholders:

Climate researchers and meteorologists

Government and policy makers

Urban planners and civil engineers

Agricultural organizations

Tourism boards

Energy and utility companies

Environmental NGOs and data analysts

Success Metrics:

Identify hot, cold, and stable regions accurately

Understand seasonal temperature patterns

Predict climate-related risks

Improve data-driven decision-making

Communicate insights clearly using dashboards

## Analytical Approach
Key Measures Created in Power BI
-- Monthly Temperature Range
Monthly Temperature Range (°C) = 
VAR MaxTemp = MAX(Unpivot_wikipedia_city_temperature_data[Avg Monthly Temp])
VAR MinTemp = MIN(Unpivot_wikipedia_city_temperature_data[Avg Monthly Temp])
RETURN MaxTemp - MinTemp

-- Climate Stability Category
Climate Stability Category = 
SWITCH(
    TRUE(),
    [Monthly Temperature Range (°C)] < 5, "Very Stable",
    [Monthly Temperature Range (°C)] < 10, "Stable",
    [Monthly Temperature Range (°C)] < 15, "Moderate",
    "Highly Volatile"
)

-- Climate Consistency Category
_Climate Consistency Category = 
VAR RangeValue = [Monthly Temperature Range (°C)]
RETURN SWITCH(
    TRUE(),
    ISBLANK(RangeValue), BLANK(),
    RangeValue <= 10, "Stable",
    RangeValue <= 20, "Moderate",
    "Extreme"
)


Other measures include:

City Heat Rank

City Temperature Variability

Quarterly Average Temperature

Avg Global Temperature

Hottest / Coldest City & Temp

Most Climate-Stable City

These measures allow dynamic ranking, classification, and visualization of climate stability and volatility.

Key Findings
Global Temperature Baseline

Average global temperature: ~17.9 °C

Warmest month globally: July (~39.8 °C)

Seasonal extremes, not averages, drive risk

Hotspot Cities

Hottest cities concentrated in Sub-Saharan Africa, Horn of Africa, Middle East

Persistent heat exposure dominates over episodic heatwaves

Example: Assab (~30.5 °C annual average)

Cold & Volatile Cities

Extreme monthly ranges in high-latitude cities: Yakutsk (~58 °C), Yellowknife (>40 °C)

Volatility, not cold, defines infrastructural and economic vulnerability

Climate Stability Insights

Most stable: Abidjan, Accra, Addis Ababa, Aden

Most volatile: Yakutsk, Fairbanks, Harbin, Ulaanbaatar

Equatorial/coastal cities exhibit natural thermal buffering; continental interiors face extreme oscillations

Country-Level Variability

Highest: United States, Canada, Russia

Lowest: Eritrea, Australia, Colombia

## Strategic Recommendations

Urban Planning & Infrastructure:

Hot, stable cities → Heat-resilient materials, reflective surfaces, urban greening

Cold, volatile cities → Design for freeze-thaw resistance and adaptive energy grids

Public Health & Safety:

Early warning systems in volatile regions

Heat-stress mitigation programs in consistently hot cities

Energy & Utilities:

Hybrid energy systems for volatile climates

Renewable energy planning in stable climates

Economic & Investment Planning:

Stable cities for long-term investments (data centers, manufacturing)

Volatile cities require higher risk buffers and insurance premiums

Policy & Climate Adaptation:

Shift from national averages to city-level metrics

Incorporate monthly temperature range into resilience indices

Future Enhancements:

Integrate humidity, heat index, and population density

Multi-year trend analysis for accelerated risk detection

## Potential Analyses

Average yearly and monthly temperatures per city

Hottest and coldest city rankings

Temperature variability by country

Seasonal temperature comparison

Climate stability vs volatility

City ranking by heat exposure

Tools Used

Power BI: For data modeling, dashboard creation, and visualization

DAX Measures: Custom calculations for stability, variability, and ranking

Data Scraping: Wikipedia for global monthly temperature data

## Conclusion

This project demonstrates that city-level temperature analysis provides far more actionable insights than national averages. By measuring stability, volatility, and extremes, stakeholders can make informed decisions across urban planning, energy, agriculture, and tourism sectors.

The dashboards allow interactive exploration, making climate intelligence accessible to policymakers, planners, and researchers alike.

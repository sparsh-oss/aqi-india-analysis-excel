# India Air Quality Index (AQI) Analysis (Excel)

An Excel analysis of daily air quality data across 26 Indian cities (2015–2020), sourced from CPCB (Central Pollution Control Board) monitoring stations, enriched with a custom City→State/Region/Zone lookup table to identify pollution patterns by geography.

## 📊 Project Overview

This project analyzes ~29,500 daily air quality records to answer:

- Which Indian cities have the worst and best air quality?
- Does air quality differ by region (North/South/East/West) or by Metro vs. Non-Metro status?
- How has national air quality trended from 2015 to 2020?

This connects to my interest in environmental and climate policy, an area I've also written about in the context of MSME sustainability practices.

## 🛠️ Tools & Techniques Used

- **Power Query** for CSV import and cleaning
- **Custom lookup table** (City → State → Region → Zone) built manually to enrich raw data lacking geographic classification
- **INDEX/MATCH** to join the lookup table into the main dataset (~29,500 rows)
- **Outlier detection and handling** using COUNTIF/MAX/MIN
- **AVERAGEIF / MEDIAN** for city, region, and zone-level summaries
- **Pivot Tables with Slicers** for interactive year and region filtering
- **Dashboard** with KPI cards and comparison charts

## 🧹 Data Cleaning Note

India's official AQI scale runs 0–500. This dataset contained **543 readings (1.8%) exceeding 500**, up to a maximum of 2,049 — likely sensor anomalies rather than genuine readings. These were excluded from a cleaned `AQI_Clean` column used throughout the analysis, since including them skewed city averages significantly (e.g., Ahmedabad's average AQI dropped from a distorted 452 to a realistic 168 after cleaning).

## 🔑 Key Findings

**Most & Least Polluted Cities (by Average AQI)**
| Rank | City | Avg AQI |
|---|---|---|
| 1 (Worst) | Delhi | 250.8 |
| 2 | Lucknow | 202.7 |
| 3 | Gurugram | 189.5 |
| ... | ... | ... |
| 25 | Shillong | 35.6 |
| 26 (Best) | Aizawl | 34.2 |

Delhi's average AQI is over **7x higher** than Aizawl's — a stark geographic divide in air quality.

**By Region**
| Region | Avg AQI |
|---|---|
| North | 184.0 |
| East | 139.1 |
| Central | 127.8 |
| West | 97.2 |
| South | 92.8 |
| Northeast | 89.3 |

North India shows by far the worst air quality, roughly double the South and Northeast — consistent with known factors like stubble burning, vehicle density, and geographic pollution trapping in the Indo-Gangetic plain.

**Metro vs. Non-Metro**
| Zone | Avg AQI |
|---|---|
| Metro | 144.7 |
| Non-Metro | 97.9 |

Metro cities show ~48% worse average air quality than non-metro cities.

**Year-over-Year National Trend**
| Year | Avg AQI |
|---|---|
| 2015 | 128.7 |
| 2016 | 138.1 |
| 2017 | 117.3 |
| 2018 | 140.2 |
| 2019 | 135.8 |
| 2020 | 105.5 |

2020 shows the lowest average AQI of the entire period — plausibly linked to reduced industrial and vehicular activity during COVID-19 lockdowns.

## 📁 Repository Contents

- `AQI_India_Analysis.xlsx` — full workbook (Raw Data, City Lookup, Analysis, Pivot Tables, Dashboard)
- `city_day.csv` — source dataset
- `city_lookup.csv` — custom-built City→State/Region/Zone reference table

## 📌 Dataset Source

[Air Quality Data in India (2015–2020)](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india) — Kaggle, sourced from the Central Pollution Control Board (CPCB)

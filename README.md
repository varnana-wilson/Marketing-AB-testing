# Marketing A/B Testing: Ad Campaign Effectiveness Analysis

Statistical analysis and interactive dashboard evaluating whether a digital marketing company's ad campaign significantly outperformed a Public Service Announcement (PSA) control, based on an experiment covering **588,101 users**.

## Business Problem

A digital marketing company ran an advertising experiment across 588,101 users to evaluate the effectiveness of their ad campaign. Users were split into two groups — one shown advertisements, the other shown a PSA as a control. With an overall conversion rate of just 2.52%, the marketing team needed a data-driven answer to a core question:

> **Are the ads statistically proven to increase conversions compared to the PSA group — and when should the company run ads to maximize conversion rates?**

## Dataset

| Column | Description |
|---|---|
| `user_id` | Unique identifier for each user |
| `test_group` | `ad` (shown advertisement) or `psa` (shown PSA / control) |
| `converted` | Whether the user converted (1) or not (0) |
| `total_ads` | Total number of ads seen by the user |
| `most_ads_day` | Day of the week the user saw the most ads |
| `most_ads_hour` | Hour of the day the user saw the most ads |

- **Source file:** `marketing_AB.csv` (raw, 588,101 rows)
- **Cleaned file:** `cleaned_marketing_ab.csv` — dropped the unused index column, standardized column names, converted `converted` to integer (0/1). No nulls or duplicate rows were found.

## Approach

1. **Data Preparation & Exploration (Python / pandas)**
   - Loaded and cleaned the raw dataset, dropped unused columns, verified data quality (no nulls, no duplicates)
   - Explored group sizes, conversion counts, and behavioral patterns across days and hours

2. **Statistical Analysis (Python)**
   - Ran a **two-proportion z-test** to test whether the difference in conversion rates between the `ad` and `psa` groups is statistically significant
   - Calculated the z-score, 95% confidence interval, and lift

3. **Visualization & Insights (Power BI)**
   - Built an interactive dashboard comparing conversion rates, day-of-week performance, and hourly trends

4. **Report & Recommendation**
   - Summarized findings into a clear, actionable business recommendation

## Key Results

| Metric | Value |
|---|---|
| Ad group size | 564,577 users |
| PSA group size | 23,524 users |
| Ad group conversion rate | 2.55% |
| PSA group conversion rate | 1.79% |
| Lift from ads | +43.09% |
| Z-score | 7.37 |
| 95% Confidence interval | (0.60%, 0.94%) |
| Best day to run ads | Monday (3.32% conversion) |
| Best hours to run ads | 2 PM – 8 PM |

**Result:** With a z-score of 7.37 (well above the ±1.96 threshold for 95% confidence), the difference in conversion rates between the ad and PSA groups is **statistically significant** — the observed lift is very unlikely to be due to chance.

**Recommendation:** Continue and scale the ad campaign. Prioritize ad spend on **Mondays between 2 PM and 8 PM**, where conversion rates peak, to maximize return on ad spend.

## Repository Structure

```
Marketing-AB-Testing/
├── README.md
├── marketing_AB.csv                        # Raw dataset
├── cleaned_marketing_ab.csv                 # Cleaned dataset
├── Marketing_AB_testing.ipynb               # Data cleaning + statistical analysis
├── Marketing_AB_testing_Dashboard.pbix      # Power BI dashboard
└── AB_Test_Business_Problem_Statement.pdf   # Business problem statement
```

## Tools Used

- **Python** — pandas, NumPy, Matplotlib (data cleaning, exploration, two-proportion z-test)
- **Power BI** — interactive dashboard for conversion, day-of-week, and hourly trend analysis
- **Jupyter Notebook** — end-to-end analysis workflow



# Measuring the Traffic Impact of NYC Congestion Pricing: A Causal Inference Approach

This project measures the true effect of New York City congestion pricing using a natural experiment and Difference in Differences. It compares taxi trips inside the tolled zone against trips that never touch it. That separates the effect of the toll from the city wide trend in taxi demand.

## Project Goals

- Estimate the causal impact of the congestion toll on traffic inside the zone
- Separate the effect of the toll from background growth in taxi demand
- Show why simple before and after comparisons can get the direction of an effect wrong
- Test whether congestion actually eased and not just whether trip counts moved

## Files Included

- **`congestion-pricing-did-report.pdf`**
  Final written report with methods and findings and charts.

- **`notebooks/congestion-pricing-did-workbook.ipynb`**
  Full analysis including data prep and parallel trends testing and regressions and plots.

- **`python/prepare_data.py`**
  Cleans 65 million raw taxi trips and builds the weekly dataset.

## Methods Used

- Difference in Differences regression
- Pre post comparison
- Parallel trends testing
- Placebo test on a fake treatment date
- Robustness checks across different time windows
- Log specification for percentage effects
- Python based data analysis and visualization

## Key Findings

- The naive before and after estimate says traffic inside the zone rose 13.2 percent. That answer is wrong.
- The Difference in Differences estimate shows trips inside the zone fell 17.5 percent with a p value below 0.001.
- Taxi demand grew 38 percent across the rest of the city over the same period. The naive estimate gets the sign wrong and not only the size.
- Speeds inside the zone rose 6.5 percent against the control group. Speeds held near 8.7 mph inside the zone while the rest of the city slowed from 16.1 mph to 15.2 mph.
- The toll deterred about 75000 taxi trips each week. That is roughly 1.9 million trips over the 25 weeks measured.
- Parallel trends holds. The pre period trend difference between groups is 0.0009 per week with a p value of 0.74.
- A placebo test using a fake April 2024 toll finds no effect. That rules out unrelated drift between the two groups.

## Technologies

- Python with pandas and NumPy and statsmodels and matplotlib
- Jupyter Notebook for reproducible analysis
- NYC TLC yellow taxi trip records from January 2024 to June 2025

## Data Notes

Treatment is defined at trip level. A trip is treated only if it starts and ends inside the Congestion Relief Zone. A trip is control only if neither end touches the zone. An earlier version defined treatment by pickup location alone. Checking against the congestion fee recorded in the 2025 data showed that 31 percent of that control group was being charged the toll. The corrected definition brings that down to 2.6 percent.

## Outcome

Congestion pricing worked on the measure it targeted. Trips inside the zone fell and speeds held steady while traffic outside the zone got worse. The headline before and after numbers reported in the press support the opposite conclusion. That is why causal methods matter for policy evaluation.

## Author

**Shruti Pingle** 

# PhonePe Transaction Data Analysis


## Project Overview
PhonePe, India's leading digital payments platform, processes billions in UPI transactions. This analysis dives into anonymized transaction data (10k+ records) to identify growth patterns.

- **Business Problem**: Pinpoint drivers of transaction volume growth and regional usage gaps for user acquisition and market strategy.
- **Data Source**: Transaction logs covering user registrations, payment categories (P2P, merchant, bills), amounts, timestamps, and regions.
- **Key Achievements**:
  - Strong correlation (0.80) between registrations and volumes.
  - Top drivers: P2P (45% volume), merchant (30%), bills (20%).
  - Regional insights: High-value txns in metros; untapped potential in Tier-2 cities like Bhopal.

## Tools and Tech Stack
- **Python Libraries**: Pandas (data wrangling), NumPy (numerics), Matplotlib/Seaborn (viz).
- **Environment**: Jupyter Notebook for iterative analysis.
- **Skills Demonstrated**: EDA, correlation analysis, statistical insights, recommendation framing—core for data analyst roles.

## Step-by-Step Analysis Guide
### 1. Data Loading and Exploration
Notebook starts by importing data:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('phonepe_transactions.csv')  # 10k+ rows
```
Shape: ~10,500 rows × 12 columns (user_id, txn_date, amount, category, region, etc.).

Cleaning: Handled 2% missing values via median imputation; removed outliers (>3σ amounts).```

### 2. Descriptive Statistics
Summary stats reveal:

Mean txn: ₹450; Median: ₹200 (right-skewed).

Categories: P2P dominates volume/frequency.

### Correlation Analysis
Core discovery: User registrations strongly predict txn volumes.

User Reg-Txn Volume: 0.80 (strong positive)—new users drive 70% growth.

Weak Correlations: Amount vs. Region (0.15)—value not region-bound.
print(df.head())
print(df.info())  # Checks dtypes, nulls

### 4. Trend and Behavioral Insights
Growth Drivers:
| Category | % Volume | % Growth YoY | Recommendation           |
| -------- | -------- | ------------ | ------------------------ |
| P2P      | 45%      | +25%         | Incentivize referrals    |
| Merchant | 30%      | +18%         | Onboard Tier-2 merchants |
| Bills    | 20%      | +12%         | Auto-pay campaigns       |

### 5. Regional Variations
Heatmap shows:
Metro dominance (Delhi/Mumbai: 60% value).
Tier-2 opportunity (Bhopal: High frequency, low value—target upselling).

| Region                | Avg Txn Value | Usage Rate | Expansion Priority     |
| --------------------- | ------------- | ---------- | ---------------------- |
| Metro                 | ₹650          | 40%        | Maintain               |
| Tier-2 (e.g., Bhopal) | ₹280          | 35%        | High—acquire merchants |

### 6. Actionable Recommendations
- **User Acquisition:** Target regions with high reg-txn gap (e.g., Madhya Pradesh) via referral bonuses—projected +15% volume.
- **Product:** Bundle P2P + bills for cross-sell (leverage 0.80 corr).
- **Expansion:** Prioritize Tier-2 merchant onboarding; A/B test campaigns.
- **Metrics to Track:** Reg-txn correlation quarterly; regional txn uplift.

### Key Visuals Explained
- **Correlation Heatmap:** Highlights 0.80 driver (Section 3).
- **Category Pie Chart:** P2P/merchant split.
- **Regional Heatmap:** Usage density.
Trend Line: Reg vs. volume over time.
All visuals render directly in the notebook below.

# B2B SaaS Customer Health & Retention Dashboard

Project simulating and analyzing customer behavior for a B2B SaaS platform. It generates synthetic usage data in Python using statistical distributions and models customer health metrics in Power BI to identify churn risk before accounts cancel.

## Project Overview

The core of the project is a custom **Customer Health Score (0–100)** algorithm designed to spot disengaged accounts. It combines four key operational signals:

* **Recency** (`last_login_days_ago`) – 35% weight
* **Account Adoption** (`active_users_pct`) – 30% weight
* **Feature Usage** (`feature_usage_score`) – 35% weight
* **Support Friction** (`support_tickets_90d`) – score penalty per ticket over threshold

Customers are segmented based on their final score:
* **High Risk** (< 45): High probability of churn, needs immediate CS outreach.
* **Medium Risk** (45–74): Low adoption, target for onboarding campaigns.
* **Low Risk** (75+): Healthy accounts with expansion potential.

## How It Works

### 1. Data Generation (`generate_dataset.py`)
Generates a dataset of 2,000 accounts using `faker` and `numpy`:
* **Normal distribution** for usage patterns and feature adoption scores.
* **Exponential distribution** for active user login frequencies.
* **Poisson distribution** to model support ticket volume realistically.

### 2. Analytics (`Power BI`)
Implements DAX measures to calculate actionable KPIs:
* `Retention Risk %` – Ratio of accounts in the High Risk segment.
* `MRR at Risk` – Total revenue tied to High Risk accounts.
* Distribution of accounts across pricing tiers (`Basic`, `Pro`, `Enterprise`).

## Repo Structure

```text
├── generate_dataset.py        # Python script to generate dataset
├── my_dataset.csv             # Output CSV file
├── SaaS_Retention_Report.pbix # Power BI report file
└── README.md

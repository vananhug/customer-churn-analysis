# 💎 Luxury Under the Microscope: Customer Churn & Digital Strategy Analysis
## Introduction 
This project is part of a practical course in my university program, which I completed with my colleagues. This project analyses customer behaviour for a luxury distributor in California, USA to understand the mechanisms of customer churn in their stores. The study specifically investigates if digital tools (mobile app, chatbots, e-newsletters) build loyalty or contribute to churn, and provides data-driven recommendations for business strategy
## Objectives: 
- **Identify Churn Factors:** Determine which factors lead to the termination of the customer relationship.
- **Evaluate Digital Tools:** Assess the impact of mobile apps, chatbots, and newsletters on purchase frequency and cart abandonment.
- **Customer Segmentation:** Group customers based on demographics and behaviour to tailor marketing strategies.
- **Predictive Modelling:** Build models to classify customers and score their risk of leaving
## Methodology and Tech Stacks: 
**1. Data Cleaning & EDA**
  - **Logic Verification:** Checked for data consistency (e.g., age vs. education, income vs. expenses)
  - **Outlier Analysis:** Used both Quartile methods and LOF (Local Outlier Factor).
    - Adopted a conservative approach, removing only illogical errors while keeping high-income/high-expense outliers, as they represent valuable "luxury" clients
  - **Imputation:** Handled missing data using the MICE package (Multivariate Imputation by Chained Equations).
    - Predictive Mean Matching (PMM) was chosen over simple mean/median or standard regression as it best preserved the variance and original data structure
    
**2. Feature Engineering & Transformation**
  - **Transformation:** Applied Yeo-Johnson transformation for skewed variables (e.g., catalogue purchases) and Log transformation for total expenses after analysing coefficients of variation
  - **Clustering:** Performed Hierarchical Clustering using Ward’s method with Euclidean distance to identify distinct customer personas

**3. Modeling**
  - **k-Nearest Neighbours (k-NN):**
    - Selected features: Annual Household Income and Average Ad Watch Time.
    - Achieved 70% accuracy on the test set with k=13.
  - **Risk Scoring Model:**
    - Develop a custom scoring system (0-9 points) based on 5 binary criteria:
      - ***+4 points:*** No purchase in >3 average cycles (Critical factor).
      - ***+2 points:*** Below-average web visits.
      - ***+1 point* each:** No newsletter, no search usage, no app usage
    - Categorise customers into 3 churn risk groups: 0-2: Low risk, 3-6: Medium risk, 7-9: High risk
## Key Results & Customer Segments:
The analysis identified 4 distinct customer profiles
| Segment| Characteristics | Risk Level |
| ------------- | ------------- | ------------- |
| 1 | Older (55+), wealthy, loyal to offline/catalogue channels. High spending | Low |
| 2 | Middle-aged, moderate income, conservative shoppers. High need for information. | **High** |
| 3 | Young (<40), low income, high digital activity (app/bot) but low conversion. | **High** |
| 4 | Average demographics, multichannel users, frequent cart abandonment. | Medium |

**Critical Insight:** High digital activity does not equate to sales. Segment 3 interacts heavily with the app and chatbot but has the lowest spending and high churn risk, often treating the online store as a browsing tool rather than a shopping channel
## Recommendation 
The data supported two opposing strategic directions for the business conclusion:
1. Scenario A: Shut down or minimise the e-commerce channel. Data shows the most profitable segment (Class 1) prefers offline/catalogue. Online channels attract low-value traffic (Class 3) that drains resources.
2. Scenario B (The "Modernisation" Approach): Overhaul the digital strategy using "Storyselling". Since Class 3 is young and digitally active but low-spending, the goal is to monetise their attention through high-end content marketing and personalised UX, rather than treating the app as a simple catalogue.


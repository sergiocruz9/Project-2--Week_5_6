# Project 2 – Week 5–6  
## Vanguard A/B Test Analysis

Analysis of Vanguard's digital interface redesign experiment to determine if a new UI design improves user completion rates and overall experience.

---

## Project Overview

- **Period:** March 15, 2017 – June 20, 2017  
- **Objective:**  
  Evaluate whether a redesigned online process increases client completion rates by **at least 5%** (business threshold for investing in the new design).
- **Method:**  
  Classic **A/B test**:
  - **Control Group:** Existing online process  
  - **Test Group:** New UI design for the same process
- **Online Process:**  
  Users move through 5 steps:
  1. Start  
  2. Step 1  
  3. Step 2  
  4. Step 3  
  5. Confirmation  

---

## Team

- **Group:** Group 4 – *The Datathletes*  
- **Members:**  
  - Jeremy Patole  
  - Sergio Cruz  

---

## Experiment Design & Success Criteria

- **Primary Success Criterion:**  
  - **≥ 5% improvement in completion rate** (Test vs Control) is required for Vanguard to invest in the new design.
- **Key Metrics:**
  1. **Completion Rate** – % of users who reach the final *“confirmation”* step  
  2. **Average Time Spent** – Mean time to complete the process (in minutes)  
  3. **Error Rate** – % of steps where users move **backwards** (proxy for confusion/friction)

---

## Datasets

- **Client Demographics (`df_final_demo`):**  
  - Age, gender, tenure, account details
- **Web Interactions (`df_final_web_data_pt_1`, `df_final_web_data_pt_2`):**  
  - Step-by-step user activity logs across the funnel
- **Experiment Roster (`df_final_experiment_clients`):**  
  - Client IDs and **Test / Control** group assignments

---

## Key Performance Indicators (KPIs)

1. **Completion Rate**  
   \- Numerator: # of clients who reach *“confirm”*  
   \- Denominator: # of clients who started the process  

2. **Average Time Spent**  
   \- Mean duration (in minutes) from *start* to *confirmation* for clients who completed the process  

3. **Error Rate**  
   \- % of steps classified as **backwards moves** by the client during the process  

---

## Analysis Workflow

1. **Data Cleaning & EDA**  
   - Handle missing values, validate group assignments, explore demographics and behavior patterns.
2. **Metric Calculation**  
   - Compute completion rate, average time spent, and error rate for each group (Control vs Test).
3. **Hypothesis Testing**  
   - Use appropriate statistical tests to determine if observed differences are **statistically significant** at α = 0.05.
4. **Experiment Evaluation**  
   - Compare statistical significance **and** business threshold (5% improvement on completion).
5. **Visualization**  
   - Build an interactive Tableau dashboard to explore results and segment by demographics.

---

## Hypothesis Tests Conducted

For each key metric, we tested **Control vs Test**:

1. **Completion Rate Difference**  
   - **Null (H₀):** There is **no difference** in completion rate between Control and Test.  
   - **Alternative (H₁):** There **is a difference** in completion rate between Control and Test.  
   - **Test:** Two-proportion comparison (implemented via Chi-square / z-test for proportions)  
   - **Significance Level:** α = 0.05  

2. **Error Rate Difference**  
   - **Null (H₀):** There is **no difference** in error rate between Control and Test.  
   - **Alternative (H₁):** There **is a difference** in error rate between Control and Test.  
   - **Test:** Chi-square test for proportions  
   - **Significance Level:** α = 0.05  

3. **Average Time Spent Difference**  
   - **Null (H₀):** There is **no difference** in average time spent between Control and Test.  
   - **Alternative (H₁):** There **is a difference** in average time spent between Control and Test.  
   - **Test:** Two-sample t-test  
   - **Significance Level:** α = 0.05  

4. **Cost-Effectiveness Threshold (Business Rule)**  
   - Even if differences are statistically significant, the new design must deliver at least a **5% improvement in completion rate** to be considered cost-effective.

---

## Results Summary

### 1. Completion Rate

- **Control:** 65.58%  
- **Test:** 69.30%  
- **Absolute Difference:** **+3.72 percentage points**  
- **Statistical Significance:**  
  - **p-value ≈ 5.8e-19** → **Highly significant** at α = 0.05 :contentReference[oaicite:0]{index=0}  

**Interpretation:**  
The new UI **significantly improves completion rate**, but the improvement is **3.7%**, which is **below** Vanguard’s **5% business threshold** for investment.

---

### 2. Error Rate

- **Control:** 34.40%  
- **Test:** 37.81%  
- **Absolute Difference:** **+3.41 percentage points** (worse in Test)  
- **Statistical Significance:**  
  - **p-value ≈ 2.18e-15** → **Highly significant** at α = 0.05 :contentReference[oaicite:1]{index=1}  

**Interpretation:**  
Users on the new design **make more backward moves**, suggesting **greater confusion or friction** in the redesigned interface.

---

### 3. Average Time Spent in Process

- **Control:** 6.4 minutes  
- **Test:** 7.3 minutes  
- **Difference:** **+0.9 minutes (~54 seconds)** (longer in Test)  

**Interpretation:**  
On average, clients in the Test group **take longer** to complete the process, but this difference is **not statistically significant** in our test. Still, from a UX perspective, the combination of **more errors** and **no clear reduction in time** is not favorable.

---

## Overall Conclusions

- The new design **does improve completion rate**, but only by **3.7%**, **below** the **5% improvement threshold** Vanguard requires to justify investment.  
- The new design is associated with a **higher error rate**, indicating more confusion or friction.  
- There is **no statistically significant improvement in time** spent; if anything, the trend suggests users may spend **more** time with the new design.

> **Therefore: we do *not* recommend investing in the new design in its current form.**

---

## Business Recommendations

1. **Do Not Roll Out the New Design Yet**
   - Despite a statistically significant increase in completion rate, the **business target of +5%** is **not achieved**.
   - Higher error rates and longer completion times raise concerns about user experience and potential future support costs.

2. **Revisit Step Design (Especially Early Funnel)**
   - Analyze **drop-off** and **backward navigation** patterns, particularly at:
     - **Start**
     - **Step 1**
   - Identify confusing copy, layout issues, or excessive information load that might be causing friction.

3. **Reduce Process Time**
   - Investigate what happens at the **confirmation step** and later stages:
     - Are users re-reading information?
     - Are there too many fields, checks, or modal windows?
   - Aim to simplify content and interactions, especially for returning or experienced clients.

4. **Understand and Mitigate Error & Drop-off Drivers**
   - Deep-dive into:
     - Error patterns per step  
     - Device type, browser, and client segment differences  
   - Use these insights to iteratively improve UI/UX.

5. **Redesign & Re-run the A/B Test**
   - Based on insights above, **iterate on the design**:
     - Simplify high-friction steps  
     - Clarify instructions and visual hierarchy  
     - Test alternative layouts or progressive disclosure of information
   - Run a **new A/B test** with:
     - Clear primary metric: completion rate  
     - Secondary metrics: error rate, time, and step-level drop-off  
     - Same **5% improvement threshold** as the business decision rule.

---

## Data Quality Issues

- **Missing User Variation Group Assignment:**  
  - Some records lacked clear Control/Test assignment and should be handled carefully before inclusion in experiment analysis.
- **Missing Gender Data:**  
  - A subset of clients had missing gender information, which can limit demographic segmentation and should be documented when interpreting subgroup results.

---

## Visualizations

An interactive Tableau dashboard was built to support exploration and presentation of the results.

**Dashboard Features:**

- Completion rate comparison (Control vs Test)  
- Time spent analysis by step  
- Error rate visualization across the funnel  
- Demographic filters:
  - Age  
  - Gender  
  - Tenure  

---

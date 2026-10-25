# Employee Attrition Analysis and Prediction

MSDS 6306: Doing Data Science | Case Study 1  
Yongjoon Cho | October 25, 2026

## Executive Summary

DDSAnalytics was tasked with helping Frito Lay identify factors associated with employee attrition, predict which employees are at risk of leaving, and assess the potential financial impact of targeted retention incentives. The labeled dataset contains 870 employees, of whom 140 (16.09%) left and 730 (83.91%) stayed. A separate competition dataset contains 300 employees whose attrition outcomes are unknown.

Three factors stood out in the exploratory analysis:

1. Overtime: Employees reporting overtime had a 31.75% attrition rate, versus 9.71% among employees without overtime.
2. Job involvement: Employees with the lowest involvement rating had a 46.81% attrition rate, compared with 8.64% among those with the highest rating.
3. Job role: Sales Representatives had a 45.28% attrition rate, substantially higher than the overall rate of 16.09%.

These are observed associations, not evidence that changing a single factor would cause a corresponding change in attrition.

Two classification methods were evaluated: K-nearest neighbors (KNN) and Naive Bayes. The analysis used a stratified 80/20 training/holdout split and 500 repeated splits within the training data for additional validation. On the 174-employee holdout set, both models identified 20 of the 28 employees who left (71.43% sensitivity). Naive Bayes achieved higher accuracy (82.76% vs. 77.59%), specificity (84.93% vs. 78.77%), and F1 score (57.14% vs. 50.63%) than KNN. Both models exceeded 60% sensitivity and specificity on the holdout set and on their average repeated-split validation metrics. Naive Bayes was selected for the competition predictions.

The business analysis considers a $200 incentive for each flagged employee and replacement costs ranging from 50% to 400% of annual income. Under the illustrative assumption that every correctly flagged leaver accepts the incentive and stays, estimated total costs depend not only on false-positive and false-negative counts but also on the salaries of employees whose departures are missed. In the 100% annual-salary replacement-cost scenario, estimated holdout costs were $548,652 for KNN and $578,208 for Naive Bayes. These estimates are scenario calculations, not demonstrated savings; actual outcomes depend on intervention effectiveness and implementation costs.

The findings suggest prioritizing further review of overtime practices, job involvement, and retention challenges among Sales Representatives. Before deploying either classifier operationally, the company should test whether the proposed intervention actually reduces turnover and evaluate the cost of missed departures alongside unnecessary incentives.

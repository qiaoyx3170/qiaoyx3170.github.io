---
layout: post
title: HealthCloud-Intelligent Heart Disease Monitoring with Machine Learning
subtitle: A cloud-based system for predicting and monitoring heart disease using machine learning.
gh-badge: [star, fork, follow]
tags: [Cloud-Computing, AI-Healthcare]
comments: true
mathjax: true
author: Yuxi
---

With the increasing amount of online information and the development of digital technologies, people have started to rely on internet-based tools for self-diagnosis, especially after the global health crisis in 2020. However, many existing approaches—such as searching symptoms online or reading medical blogs—can often lead to misunderstanding and inaccurate conclusions. 

To address this issue, a system called [*HealthCloud*](https://github.com/iamssgill/HealthCloud) was developed to monitor the health status of heart patients using machine learning and cloud computing. The system aims to provide more reliable and data-driven predictions compared to traditional self-diagnosis methods.



## HealthCloud system

The system is based on a mobile health prediction framework that integrates a CoreML-powered machine learning model to estimate the risk of heart disease. It is implemented as an iOS application and follows the Model–View–Controller (MVC) architecture to clearly separate the user interface, control logic, and data processing components.

In the app, users manually input relevant clinical features such as blood test results and ECG measurements. Then, these inputs are processed by the embedded model, which generates a prediction of whether the user may be at risk of heart disease. 

The result is immediately displayed on the screen along with basic advice.

![Interface](https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr1_lrg.jpg)


## Data Source

The dataset used in this study is the [*Cleveland Heart Disease dataset*](https://archive.ics.uci.edu/dataset/45/heart+disease) from the UCI Machine Learning Repository. It contains 303 patient records collected from the Cleveland Clinic Foundation and has been widely used in medical machine learning research.

Before analysis, the data was properly pre-processed, including cleaning missing or inconsistent values, adjusting encoded variables to match the dataset documentation, and reorganising the data into a suitable format for machine learning. After preprocessing, the dataset was reduced to 284 usable instances and split into training and test sets for model development and evaluation.

## Machine-learning Algorithms

Five machine learning algorithms were selected and evaluated for heart disease prediction:

**Support Vector Classifier (SVC):** SVC is a margin-based classifier that finds an optimal hyperplane to separate patients with and without heart disease, making it effective for high-dimensional and unseen data. 

**K-Nearest Neighbours (KNN):** KNN classifies a patient based on the most similar cases in the dataset, using distance-based similarity measures. 

**Neural Networks (NN):** The Neural Network model uses a multi-layer perceptron structure with non-linear activation functions to capture complex relationships between features and the target variable. 

**Logistic Regression (LR):** Logistic Regression provides a probabilistic linear approach using a sigmoid function to estimate disease risk.

**Gradient Boosting Trees (GBT):** Gradient Boosting Trees is an ensemble method that builds multiple decision trees sequentially, where each tree improves the performance of the previous one, making it particularly effective for reducing bias and handling complex patterns in medical data.


## System Perfrmance

The performance of the system was evaluated using multiple methods, including standard classification metrics, cross-validation techniques, and Quality of Service (QoS) parameters, to assess both predictive performance and system efficiency.


### Classification Metrics

Classification metrics are used to evaluate how well the models perform on classification task. The metrics used are **Accuracy**, **Precision**, **Recall (Sensitivity)**, **Specificity**, **Confusion Matrix**, **ROC-AUC**, and **5-fold Cross-validation**. The results are shown as follows:

|  | Accuracy | Precision | Sensitivity | Specificity | 
| :------ |:--- | :--- | :--- | :--- |
| **SVC** | 0.8421 | 0.9565 | 0.733 | 0.963 |
| **KNN** | 0.5965 | 0.6667 | 0.467 | 0.741 |
| **NN** |  0.8421 | 0.92 | 0.767 | 0.926 |
| **LR** | 0.8596 | 0.9583 | 0.767 | 0.963 |
| **GBT** | 0.807 | 0.9524 | 0.667 | 0.963 |

<br>

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr8_lrg.jpg" width="500">

<br>

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr9_lrg.jpg" width="500">


### Ensemble Learning

Ensemble Learning is used to examine whether combining models (via bagging) could improve prediction performance. The results show that ensemble learning did not significantly improve performance and, in some cases, even reduced accuracy or increased latency：

<br>

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr10_lrg.jpg" width="500">

<br>

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr11_lrg.jpg" width="500">

### Quality of Service (QoS)

QoS parameters are used to evaluate the system from a practical deployment perspective. In this study, the QoS metrics are evaluated in terms of **Time** and **Memory usage**, where Time includes both execution time and latency. The results are shown as follows:

**Execution time & Latency**: 

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr12_lrg.jpg" width="500">

<br>

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr13_lrg.jpg" width="500">

**Memory usage**:

<img src="https://ars.els-cdn.com/content/image/1-s2.0-S2542660521001244-gr14_lrg.jpg" width="500">



## Implementation and Performance of the iOS Application

The **Logistic Regression** model was selected as the final algorithm. It was implemented in an iOS application using Apple’s CreateML and Xcode. 

The model was retrained with the target variable separated from the input features. It achieved an accuracy of 84%, a precision of 86%, and a recall of 84% on the test dataset.

# What is Imbalance Dataset?

An imbalanced dataset refers to a situation in a classification problem where the distribution of class labels is not equal or roughly equal. In other words, one class (the minority class) has significantly fewer instances than the other class or classes (the majority class or classes). This imbalance in class distribution can pose challenges for machine learning models, particularly in scenarios where the goal is to accurately predict the minority class.

Always report the prevalence of the dataset while presenting the model for review. For example, a positive prevalence of dataset 0.01 means 1 positive label per 100 instances.

A low prevalence dataset is another term for a highly imbalanced dataset.

Imbalanced datasets are common in various real-world applications, including fraud detection, anomaly detection, rare disease diagnosis, and certain types of manufacturing defects. In these situations, the occurrence of the event of interest (the positive class) is relatively rare compared to the non-occurrence (the negative class).

Dealing with imbalanced datasets is important because many machine learning algorithms are designed to maximize overall accuracy, which can lead them to favor the majority class. In imbalanced scenarios, this can result in models that perform well in terms of overall accuracy but poorly in terms of correctly identifying instances of the minority class.

# What is the AUC-ROC curve?

AUC stands for “Area Under the Curve” in general, and “Area under the Receiver Operating Characteristic Curve” in long form. It captures the area under the ROC (Receiver Operating Characteristic) curve and compares the relationship between the True Positive Rate (TPR) with that of the False Positive Rate (FPR) across different cut-off thresholds. 

A measurement tool for binary classification problems is the ROC curve especially when the dataset is imbalanced. It essentially separates the "signal" from the "noise" by plotting the TPR against the FPR at different threshold levels. The Area measures the capacity of a classifier to differentiate between classes Under the Curve (AUC), which is used as a summary of the ROC curve. 

**TPR or True Positive Rate**
 
It is the ratio of correctly predicted positive instances out of all the positive samples. For example, if the model is tasked to identify the fraudulent transactions, then TPR is defined as the proportion of correctly predicted fraudulent transactions among all fraudulent transactions.  

**FPR or False Positive Rate**

It is the percentage of incorrectly predicted negative cases. Continuing with the fraud detection model, the FPR is defined as the proportion of falsely predicted fraudulent alerts out of all the legitimate transactions. 

Mathematically, TPR and FPR are expressed as:
![image](https://github.com/senthilnsk3011/Building-Different-models-comapring/assets/40666655/f68ef373-376a-4175-9248-abf6a7d07038)


The performance of the model in differentiating between the positive and negative classes improves with increasing AUC. When the AUC is 1, the classifier can accurately discriminate between every Positive and every Negative class point. The classifier is unable to discriminate between Positive and Negative class points when the AUC value is less than 0.5.

The extremely effective Sklearn function roc curve() quickly calculates the ROC for your classifier! The FPR, TPR, and threshold values are returned.

![image](https://github.com/senthilnsk3011/Building-Different-models-comapring/assets/40666655/66b6a4c9-1f76-47c0-855a-091febb3ec31)


**Why use AUC instead of other metrics?**

AUC is well-suited for imbalanced datasets. For example, the fraud detection model must correctly identify fraud even if it comes at the cost of flagging some (a small number) of the non-fraudulent transactions as fraudulent.

It is highly probable that while focusing on correctly identifying the class of interest (fraudulent transactions) i.e. the TPs, the model makes some mistakes i.e. FPs (marking non-fraudulent transactions as fraudulent). Thus it’s important to look at a measure that compares TPR and FPR. This is where AUC fits in.

Accuracy and AUC are both used for classification models. However, there are a few things to keep in mind when you’re deciding which one to use. 

A high accuracy model indicates very few incorrect predictions. However, this doesn’t consider the business cost of those incorrect predictions. The use of accuracy metrics in such business problems abstracts away the details like TP and FP, and gives an inflated sense of confidence in model predictions that is detrimental to business objectives.

AUC is the go-to metric in such scenarios as it calibrates the trade-off between sensitivity and specificity at the best-chosen threshold. 

Further, accuracy measures how well a single model is doing, whereas AUC compares two models as well as evaluates the same model’s performance across different thresholds. 

Although ROC graphs are widely used to evaluate classifiers under presence of class imbalance, it has a drawback: under class rarity, that is, when the problem of class imbalance is associated to the presence of a low sample size of minority instances, as the estimates can be unreliable.A common alternative is the precision-recall curve and area under curve.

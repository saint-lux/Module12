# Module 12 Report

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
  * The purpose of the analysis if to use best practicies for data prerprocessing in machine learning and get better outcome; in this case, better identification of healthy vs. risky loans

* Explain what financial information the data was on, and what you needed to predict.
  * Data was on user loans. More specifically credit risk metrics such as borrower income, interest rate, loan size, debt to income etc. to determine the status of the loan (healty or risky)
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
  * I was trying to predict the status of the loan (loan_status) 0 means healthy and 1 means risky. The slight issue with the data is the data was unevenly distributed, which I determined using value_counts 75,036 healthy loans and 2,500 risky loans. This can make the model more biased towards healthy loans.

* Describe the stages of the machine learning process you went through as part of this analysis.
  * At first I split the data with an uneven number of into test and train sets without even split between healthy and risky splits.
  * Second attempt as to split the categories evenly
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1: Using Logistic Regression with uneven number of labels
    ```
    y.value_counts()

    0    75036
    1     2500
    Name: loan_status, dtype: int64
    ```
  * Description of Model 1 Accuracy, Precision, and Recall scores.

    ```
    y_test.value_counts()
    >>> 0    24744
    >>> 1      843
    >>> Name: loan_status, dtype: int64
    

    confusion_matrix(y_test,y_pred)
    >>> array([[24622,   122],
       [   82,   761]])

    # **Shows 761 1's detected correctly out of 843**
    
    array([[24622,   122],
        [   82,   761]])
    ```

                  pre       rec       spe        f1       geo       iba       sup

        0       1.00      1.00      0.90      1.00      0.95      0.91     24744
        1       0.86      0.90      1.00      0.88      0.95      0.89       843

        avg / total       0.99      0.99      0.91      0.99      0.95      0.91     25587

* Machine Learning Model 2: Logisti Regression with equal number of labels for training and testing
    ```
    y.value_counts()

    0    50292
    1    50292
    Name: loan_status, dtype: int64
    ```

  * Description of Model 2 Accuracy, Precision, and Recall scores.

  ```
  y_test.value_counts()
  >>> 0    24744
  >>> 1      843
  >>> Name: loan_status, dtype: int64
  

  confusion_matrix(y_test,y_pred)
  >>> array([[24604,   140],
       [    4,   839]])
  # ** Shows 839 1's detected correctly out of 843 **
  
  array([[24622,   122],
       [   82,   761]])
      
  ```
  
                  pre       rec       spe        f1       geo       iba       sup

        0       1.00      0.99      1.00      1.00      0.99      0.99     24744
        1       0.86      1.00      0.99      0.92      0.99      0.99       843

        avg / total       1.00      0.99      1.00      0.99      0.99      0.99     25587
## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
  * Balanced labelled model (Model2) performed better than Model 1
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )
  * Yes, the performance depend on the problem we are trying to solve. we need high accuracy per label and to get more accuracy, training data should have equal number of labels.
If you do not recommend any of the models, please justify your reasoning.

# Credit_Risk_Modelling

- Story

I want to create a scorecard to model Probability Default (PD) for real-world dataset (Freddie Mac) using Machine Learning techniques of Logistic Regression, Random Forest and XGBoosting. (Scorecard Modelling_Credit_Risk.ipynb) In addition, for PD obtained from the scorecard model, i want to try to calculate long-term PD considering prospects of macroeconomics factors. (Probability of Default Calibration.ipynb)

- Dataset used: 

Dataset includes information from the origination of the loan to predict the performance of the loan and Default flag which marks if the mortgage has defaulted.

http://www.freddiemac.com/research/datasets/sf_loanlevel_dataset.page

- Result

1. For selected configurations: (base pionts 750, minimum unit of odds: 0.01, and points needed to double the odds: 50), the scorecard is :

For example, for people with a fico score < 665, the score he/she starts with would be 647 (705-103).

```json

{'basepoints':      variable  bin  points
 0  basepoints  nan     419,
 'fico':    variable            bin    points
 20     fico   [-inf,665.0) -103.0000
 21     fico  [665.0,690.0)  -70.0000
 22     fico  [690.0,735.0)  -24.0000
 23     fico  [735.0,775.0)   30.0000
 24     fico    [775.0,inf)   84.0000,
 'servicer_name':          variable                                                bin   points
 34  servicer_name  UNITED SHORE FINANCIAL SERVICES, LLC%,%LOANDEP...  83.0000
 35  servicer_name  SUNTRUST MORTGAGE, INC.%,%GUILD MORTGAGE COMPA...  38.0000
 36  servicer_name  ARVEST CENTRAL MORTGAGE COMPANY%,%PNC BANK, NA...   9.0000
 37  servicer_name  FIFTH THIRD BANK%,%AMERIHOME MORTGAGE COMPANY,... -24.0000,
 'Area':    variable                                                bin   points
 15     Area  Pacific%,%TheDesert%,%TheNorth%,%Atlantic%,%Th...  18.0000
 16     Area                                           TheSouth -26.0000
 17     Area                                          SouthEast -46.0000,
 'cnt_borr':     variable         bin   points
 18  cnt_borr  [-inf,2.0) -26.0000
 19  cnt_borr   [2.0,inf)  38.0000,
 'dti':    variable          bin   points
 25      dti  [-inf,20.0)  45.0000
 26      dti  [20.0,30.0)  27.0000
 27      dti  [30.0,40.0)   1.0000
 28      dti   [40.0,inf) -17.0000,
 'ltv':   variable          bin   points
 0      ltv  [-inf,59.0)  31.0000
 1      ltv  [59.0,86.0)   4.0000
 2      ltv  [86.0,94.0) -12.0000
 3      ltv   [94.0,inf) -31.0000}
```

2. The scorecard distribution of the training set looks like this:

|       	|        score 	|
|------:	|-------------:	|
| count 	| 1469015.0000 	|
|  mean 	|     466.9950 	|
|   std 	|      88.7751 	|
|   min 	|     172.0000 	|
|   25% 	|     404.0000 	|
|   50% 	|     468.0000 	|
|   75% 	|     529.0000 	|
|   max 	|     718.0000 	|

3. The scorecard model is proven to be better than RF & XGB.

![ROC Curve Comparison](ROC_Comparison.png?raw=true)

4. The final scorecard cutoff (decision based on optimal predictoin and RAROC)
Reject when score <= 375
Accept when score = 400
Inspect when 367 < Score <= 400, which contains 6.7% total cases.

If jupyter notebook cannot be reviewed, please try paste the link into https://nbviewer.jupyter.org/.

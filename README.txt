---

# Machine Learning Project: FlowCap AML Classificiation DREAM Challenge

---

## Goal: Find a machine learning method to classify AML positive and healthy patients 
using FLow Cytometry data.

## Data: 2872 dataframes with 20,000 to 30,000 rows of fluorescent readings over a 
period of time (1064 seconds). Each dataframe has 8 columns: FS, SS, FL1, FL2, FL3, 
FL4, FL5, and TIME. There are 316 healthy patients and 43 AML positive patients. Each 
patient has 8 different dataframes, each which represents a tube that contains a 
different/varied cocktail of antibodies that should be able to be used to differentiate 
AML positive from negative patients. Every tube contains CD45 which is supported by the 
literature as a commonly used biomarker for AML. The 8th tube contains no antibodies and 
is used as the control. A separate dataframe is given with the AML positive/negative 
labels.

## Methodology: Aggregate and transform the data by calculating the mean of each column 
in each file. Create three different dataframes to be analyzed: mean, mean normalized 
by control, and mean log tranfsormed & normalized by control. 

## Initial Hypothesis: the dataframe with the mean log transformed and normalized by 
the control will give the best results. 
  
  ** Note that this was disproved - see the code below. 
  
## Re-evaluated Hypothesis: the dataframe that only calculated the mean will give 
the best results because this dataframe has the greatest amount of variance between
the AML postiive and healthy patients.
  
  ** Note that this was supported by the code and results below. 
  ** Note that the mean control-normalized data was also analyzed; however, it was 
  not as successful as the mean non-normalized data.
  
## Results: The best method for classification was bagged tree classification using
features FS, SS, and FL3 (supported by recursive feature selection). The result was 
an AUC 0.789 and accuracy of 0.8967. 

## Future: Using flow cytometry specific data analysis packages could increase 
accuracy and AUC significantly (most DREAM challanege winners used flow-specific packages).


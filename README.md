### Problem Statement

I am a data scientist that has been tasked with creating a model that can predict if a host on airbnb is a superhost or not. This is very important because the label superhost evokes trust in renters and customers. One big feature that decides if a host is a superhost or not is the comments. It would take way too much time for someone to look over all the comments so instead I want to create a model that can use the comments feature with others to classify a host as a superhost or not. 

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|host_is_superhost|int|modelling_dataframe|The values are either t or f that are superhost or regular host.| 
|comments|object|modelling_dataframe|Renters comments about the host.| 
|host_response_time|float|modelling_dataframe|How fast the host responds to renter.| 
|host_response_rate|float|modelling_dataframe|the proportion of times the host responds to renters.| 
|review_scores_rating|float|modelling_dataframe|Review out of 5 given by renters.| 
|reviews_per_month|float|modelling_dataframe|How many reviews a host gets a month from renters.| 

The data-set has 6 columns that were joined from three different csvs using sql. The features are being used to predict if the host is a superhost or not. 

### Analysis Summary

Analyzing the data gave me an understanding on what parts of the data can be useful to help create a model that can predict if a host is a superhost or not. When looking at data the first important part is the column that would be the y-variable, which is what the model has to predict. This was the host_is_superhost column that gives t or f for true or false. The second is what columns should be used for the X-variable. I chose features that had the most to do with the host because the what we are trying to predict is linked with host. One hhurdle was I had to use sql to join these columns together because they were in different csvs. The next was I had to change the type of one of the columns from object to float. 

I created a comment_word_count column to look at the number of words in each comment. I then used group by to find the average number of words in comments for superhost and regular hosts. superhost comments on average contained on 1700 more words than regular host comments. I then did train-test-split with X = the predicting features and y = host_is_superhost. I then used CountVectorizer to create a dataframe of words used in the data's title. I then analyzed the dataframe finding the top 25 words found and looked at CountVectorizer stop_words.

I then created many different models with their purpose being able to use the words in comments and other features to predict if a host is a superhost or a regular host. I used a pipeline to use CountVectorizer with each classifier. I only had one feature I wanted to use CountVectorizer on, because of this I used column transformation and chose the one column to use CountVectorizer on. When looking at the scores of different models the three basic models that did the best were Logistic Regression,AdaBoostClassifier,and BaggingClassifier. The best out of these three was AdaBoostClassifier.

### Conclusions/Recommendations

I also added to the basic models by creating stack models and using the three best performing models, but when looking at all the different models created the best was an AdaBoostClassifier with column transformation CountVectorizer. It had the highest test score and was the best fit model. The training score was 0.757, testing score was 0.736 and the specificity was 0.752, which means the model predicted true negatives correctly 75.2% of the time. Some recommendations I would make is a clearer definition of what makes a superhost because airbnb's explanation of what makes a superhost was not very specific. The second is finding more data features that measure host's aptitude. The third is I would look at different states to see how well hosts are liked in different states. 
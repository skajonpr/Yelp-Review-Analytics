# Yelp-Review-Analytics

## Introduction

Yelp is an American multinational corporation founded in 2004 which aimed to help people locate local businesses based on social networking. The main purpose of Yelp is to provide a platform for customers to write reviews along with providing star-ratings. Information on Yelp is reliable, up-to-date and has a wide coverage of all kinds of businesses. Millions of people use Yelp, and empirical data demonstrated that Yelp reviews affected consumers' food choice decision-making. 

In this study, it is aimed to answer questions such as what make a café good?, what are the major concerns of customers regarding a café? and how can a cafe/coffee shop improve its business operation based on customer feedbacks?, as well as other knowledge that can be extracted from the customer review. Python3 and libraries was used to manipulate data and conduct analytics. 

## Web mining

Reviews and information regarding to coffee shop/cafe specifically in Manhattan were scraped from Yelp and stored in a csv format as shown in an example below.

<img width="568" alt="scraped reviews example" src="https://user-images.githubusercontent.com/45326221/58771210-1a7a4c80-85dd-11e9-8431-236e8e38e1eb.PNG">

## Exploratory Data Analytics

### Review length analytics

This part is to study how review lengths differ across the star rating and how review lengths correlate with thier funny, useful, and cool score.

Bar chart, box plot, and heatmap are generated for visualization.

<img width="726" alt="review length barchart" src="https://user-images.githubusercontent.com/45326221/58773441-413d8080-85e7-11e9-8179-ce667800e225.PNG">

<img width="331" alt="review length bax plot" src="https://user-images.githubusercontent.com/45326221/58773452-4ac6e880-85e7-11e9-97dc-80180f19d839.PNG">

From the bar chart and box plot above, the distribution of each star rating tends to be skewed right and has a length range roughly 0 to 2000 words. It seems that there is not a significant difference of review lengths over individual ratings.

<img width="335" alt="heatmap" src="https://user-images.githubusercontent.com/45326221/58773477-616d3f80-85e7-11e9-945e-ac4c7c592688.PNG">

From the heatmap showing correlation above, it seems that funny, useful, and cool score are highly and possitively correlated, meaning if one of them in a review has a high score, the others two tend to be high too. However, there is no correlation between review lengths and all those scores. Hence, it can be concluded that longer review lengths might not give useful, funny, and cool information. 

### Seasonal Order trending Analytics

This section is to extract information from the review to see how orders differ across seasons focused on Summer and Winter. Bigram and most frequent bigrams were generated, and bar charts are used for visualization.

<img width="631" alt="seasonal trending order chart" src="https://user-images.githubusercontent.com/45326221/58774582-65e82700-85ec-11e9-918a-86d44613743b.PNG">

Unsurprisingly, cold drinks were ordered mostly in summer, and hot drinks were ordered mostly in winter.

### Geographic Mapping

As latitudes and longitudes of each cafe/coffee shop were scraped, we can generate geographical visualizaiton to see how cafes/coffee shops with their ratings distribute across Manhattan. Folium library was used to generate a map as shown below.

<img width="484" alt="Folium Graphical Visualization" src="https://user-images.githubusercontent.com/45326221/58775113-363a1e80-85ee-11e9-8619-0efdef06f3fe.PNG">

## Topic Classification

Since classification is supervised learning, a training dataset is needed. I used an external dataset with labels that was obtained from an online source to train and test models. The labels/topics in the dataset have 5 features consisting of food, service, price, anecdotes/miscellaneous and ambience as shown in the sample set below. The dataset was split into 70:30. 70 percent was used to train, and 30 percent was used to test.

Below is an example of external dataset from an online source[(link)](http://metashare.ilsp.gr:8080/login/?next=/repository/download/479d18c0625011e38685842b2b6a04d72cb57ba6c07743b9879d1a04e72185b8/). 

<img width="527" alt="training dataset" src="https://user-images.githubusercontent.com/45326221/58783448-1fee8b80-860b-11e9-9871-3a0ee2869539.PNG">

In my models, I utilized one-vs-rest strategy to implement Multi Label classification. I've conducted evaluation on 3 models including Naive Bayes, Support vector machine, and K-nearest neighbor.

### Multinomial Naïve Bayes(NB) Model

For the Naïve Bayes, several parameters were tuned to get the best performance from the model. I’ve tried using stopwords and without using stopwords and also several numbers of min_df in the tf-idf vectorization process. Also, different alpha values (Laplace smoothing value) were tuned in the Naïve Bayes model. The performance was reported as shown below.

<img width="478" alt="Naive bayes Report" src="https://user-images.githubusercontent.com/45326221/58783838-22051a00-860c-11e9-9031-be8435d1c89c.PNG">

### Support Vector Machine(SVM) Model

In the support vector machine model, linear kernel was used. After trying several numbers of C values, the performance of the model is reported as shown below. Support vector machine produced the best performance of 76% compared to the other two models that were evaluated.

<img width="541" alt="SVM report" src="https://user-images.githubusercontent.com/45326221/58796319-2e4aa080-8627-11e9-8143-83c8ca4d7781.PNG">

### K-Nearest Neighbor(KNN) Model

In K-nearest neighbour model, several numbers of K values were tuned. The performance of KNN is reported as shown below.

<img width="472" alt="KNN report" src="https://user-images.githubusercontent.com/45326221/58810271-d1131700-8647-11e9-9134-0d552dcb39d2.PNG">


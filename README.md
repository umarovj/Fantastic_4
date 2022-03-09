# Fantastic_4

## The group topic

Housing market in United States. 

## The data source used for the topic

https://www.slideshare.net/PawanShivhare1/predicting-king-county-house-prices

## The group hypothesis

Hypothesis and Goal:

The housing market is an integral part of millions of Americans' lives. A home isn’t just where one’s heart is, it is also where we spend most of our time, especially in the age of COVID. It should then be clear why, in part, determining a potential home’s worth is so important. Too high a price will crowd many out of the market, and a particularly low price could be an indicator of a potential problem with the home itself. What is ultimately optimal is variant between individuals, but the main question for all potential buyers remains: “How much is this house worth?”

For our project, we will be answering just that. We will be performing general analysis of the various factors that determine housing prices. More specifically, we believe that we can accurately predict a home’s price given a specific set of parameters. To begin, we found house sales data from King Country, Washington. Using this data, we will be constructing a machine learning linear regression line and a neural network algorithm to accurately predict a home’s price given multiple parameters such as the number of bedrooms, square footage, and location to name a few. The type of machine learning we will be employing is a standard Multilinear Regression model with housing price as our target variable and the earlier mentioned parameters like the number of bedrooms as our dependent variables. For our neural network portion, we will set up a Keras model and acquire its accuracy score under the same parameters.

As mentioned, our project will rely heavily on machine learning for the results regarding our analysis. Still, additional resources and technology will be used. We will display our visualizations through Tableau to help the viewers understand the data we are working with. All of our projects essentials are then set up and organized with HTML as a web page. 

## The group's thought on what approach they may want to use for analysis (i.e. what ML technique we may want to use to investigate the hypothesis)

ML technique - Multi-linear Regression

Applicaitons/Languages to be used:

Tableu - Map Visulization, Charts, visual data comparison, Tableu Public for web application. 

Javascript - MapBox, creating a website with application integrated

Juptyer Notebook/google Colab - Matplotlib, data processing


## Storing Our Data

The primary source of data used for our analysis would be a csv file on homes sold in Kings County. We took this dataset and uploaded into a Jupyter Notebook originally before converting it into a dataframe for easier manipulation. Afterwards, we created a Google Colab environment for the future to make appropriate edits and analysis easier for all parties involved.

![image](https://user-images.githubusercontent.com/91284661/154810009-9b066cb1-5479-4c8d-8d08-e3c98bbec665.png)

After importing our dependencies, the first step is to ensure that our data was not corrupted upon transfer. From a locally saved filepath, the csv file was imported into a dataframe and upon a glance is indeed showing up correctly.

![image](https://user-images.githubusercontent.com/91284661/154810027-a83736e0-1f4b-4bb1-8c89-4cea75312333.png)

## Key Summary Stats

Now our analysis can begin in earnest, to begin, we will use various functions starting with .describe() to achieve some baseline-readings of the contents of our data.

![image](https://user-images.githubusercontent.com/91284661/154810046-d05e2b3e-e0dc-498b-87db-c498d5df4958.png)

The exact contents of our quick analysis at-a-glance might better be viewed through the various histograms several cells later in our notebook we created. Still, to go into detail a bit, the first thing to note is that with few exceptions the count for each variable within our dataset is the same at 21,613 meaning there are few cells without data on them. Beyond this, summary statistics such as the std or standard deviation and mean will indicate variance potential skew and bias within each measurement.

![image](https://user-images.githubusercontent.com/91284661/154810065-34699061-3808-4fc3-b9e7-8a0ae23ed16e.png)

Such skew is present in our target variable, price shown in the histogram above. From viewing this, we can tell that there are significant data points on the higher end of the price index causing a large bias in our data directed towards higher prices.

## Goals and Analysis

With a general idea of how our data-frame works we were left refining exactly what we wanted to understand for this project. To begin, we looked back over our data to determine which factors seemed more pertinent to a general analysis on which factors are more relevant to a property’s value aka price. While asking these questions we also began to gather an understanding of just how we would ultimately clean up our data as part of this overall process.

![image](https://user-images.githubusercontent.com/91284661/154810092-54813974-0c13-4acc-9f20-94b7b0f23511.png)

To begin, we identified potential variable types (view and id) as redundant info to be dropped. On top of this, various other parameters such as lat and long were identified as less relevant for our analysis. This left the variables highlighted in green as more significant in the first part of our analysis. From these targeted variables, we were in essence gathering the building blocks to our machine learning algorithm that would be the base of our project.

## **Linear Regression**

After going through our data, we decided to create a linear regression to better understand how our different subsets of data interact with our target variable, price. To begin, a simple regression was formed between bedrooms and price. Upon compiling this code, summary statistics were also generated to effectively evaluate the strength of our linear regression chiefly the R-squared (**R^2**) measurement as well as Root Mean Squared Error (**RMSE**). It is also worth noting that though bedrooms were chosen as the first metric to evaluate against price, any dependent variable could be used in place of bedrooms.

![image](https://user-images.githubusercontent.com/91284661/157297357-ec3a0fe4-7201-40ef-9dd7-7471a0ad09bc.png)

Following our regression, the summary stats were displayed in the table below in conjunction with the intercept of and coefficient for our linear regression.

![image](https://user-images.githubusercontent.com/91284661/157297424-b4c37af9-b3ad-4696-a402-d10bef7d30b2.png)

As mentioned and shown when we were first examining our data, we are working with more than one dependent variable however – bedrooms is just one metric we can draw from to try and understand the price of a house. Because of this, we are ultimately determined to create a linear regression with Multiple Dependencies. So instead of our model forming a standard, y=mx+B as our simple linear regression would, our new model will take the shape of: y= m_i x_i+ ...+m_N x_N+b where N is the number of dependent variables. There are many reasons for choosing this approach, the primary being that additional data will increase the strength of our model (as determined by an increase in the (R^2) value. This also makes sense on an intuitive level as one can readily understand how there are numerous considerations to make when deciding something as important as buying a house: it seldom if ever has come down to the number of bedrooms.

There is a tradeoff in adding additional data to our model, though it has the potential to increase the strength of your regression model, it also has the power to add additional levels of bias. To account for this bias, and in doing so help us construct our Linear Regression, a correlation chart was built to find the correlation between each of our data types.

![image](https://user-images.githubusercontent.com/91284661/157297546-c9533f8c-2688-4d0d-86d8-bf4bb927e07c.png)

![image](https://user-images.githubusercontent.com/91284661/157297577-546b063a-d19c-40f6-ba71-ec36b6dfc9c3.png)

It was a combination of our correlation charts and the initial finding when we first visualized and examined the data that allowed us to make our decisions in constructing our final Linear Regression model. Still, there was one other final step to make: an adjusted R-Squared Value (**Adj-R^2**). The sequence was defined below and used as a replacement to our standard R^2 ultimately serving as an additional precaution to improve accuracy within our model.

Combined all together, our Linear Regression Model ended up containing our parameters, 'bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'view', 'grade', and 'yr_built'.

![image](https://user-images.githubusercontent.com/91284661/157297677-19d6800b-9b04-4185-a39c-6643f8c5e586.png)

In conclusion, after examining all appropriate variables we found the variable that had the biggest impact on price. According to the correlation matrix, the living square footage ("living_sqft") is shown to impact the price the most with a correlation coefficient of 0.71. The second most impactful variable was construction and design "grade" with a correlation coefficient of 0.67. 

## Machine Learning

Along with the Single and Multiple Regression we decided to create a machine learning(ML) model to try and predict the price of a house(output) given certain pieces of data. We decided on a Keras ML model but before we set that up, we preprocessed the data by selecting the following data points for our inputs; bedrooms, bathrooms, square foot living, square foot lot, floors, waterfront, condition, grade, year built, and zip code and we use the MinMaxScaler to scale our model. With the preprocessed data we setup the ML model with 4 dense layers, 19 neurons in the first 3 layers and a single neuron in the last layer. We used the relu activation function and the Adam optimizer for the model due to its efficiency with a large number of parameters in our dataset. The ML model worked through 400 epochs and came up a mean absolute error of $129,490 and an explained variance score of 70.27% meaning our algorithm is about 70% accurate based on our data with a mean error of about $130,000. If we look at a random house in our dataset we can see our model is predicting a price of about $380,700, whereas our actual sale price was $323,000. Although our price prediction was about $60,000 off it predicts the price fairly well and with more neighborhood specific data we believe we could make a more accurate ML model.
![This is an image](https://github.com/umarovj/Fantastic_4/blob/main/Resources/Keras%20model.PNG)
![This is an image](https://github.com/umarovj/Fantastic_4/blob/main/Resources/price%20prediction.PNG)
![This is an image](https://github.com/umarovj/Fantastic_4/blob/main/Resources/Sale%20Price.PNG)

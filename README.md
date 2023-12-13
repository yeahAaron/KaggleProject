## Goal of this Competition
The goal of this competition is to analyze horse racing tactics, drafting strategies, and path efficiency.

## Project Description
In this competition, you will create a model to interpret one aspect of this new data accessing X/Y coordinate mapping of horses during races. Using the data, you might analyze jockey decision making, compare race surfaces, or measure the relative importance of drafting. With considerable data, contestants can flex their creativity problem solving skills.

**Kaggle webpage that contains all of the data:**
https://www.kaggle.com/competitions/big-data-derby-2022/data

## Project Specification
* I created linear/logistic regression models and a random forest model to see if `trakus_index`, `latitude`, and `longitude` were good predictors of a horse's `position_at_finish`
    * `trakus_index` - The common collection of point of the lat / long of the horse in the race passed as an integer. From what we can tell, it's collected every 0.25 seconds.
    * `latitude` - The latitude of the horse in the race passed as a float.
    * `longitude` - The longitude of the horse in the race passed as a float.
    * `position_at_finish` - An integer of the horse's finishing position.
* Another feature that was taken into account:
    `track_id` - 3 character id for the track the race took place at. AQU -Aqueduct, BEL - Belmont, SAR - Saratoga.
    
## Data Visualization
I created a scatterplot of the linear regression model to interpret the results

### Results
* The first thing I did was update my dataframe to only containing races that took place at the Belmont track. I then updated the dataframe one more time to where the `trakus_index` of each row was equal to 40 that way I could look at the first 10 seconds of each race to see if that was a good predictor of the horses' `position_at_finish`

* Using scikit-learn, I trained and tested my data with a test size of 20%, and that allowed me to create each of the three models

X - `trakus_index`, `latitude`, `longitude`

y - `position_at_finish`

**Linear regression and random forest models:**
* I calculated the mean square error (MSE) and coefficient of determination for both models. Unfortunately, the MSE for both models was fairly high and the R2 for both models was fairly low
  
             Method	             Train MSE	  Train R2	Test MSE	 Test R2

0	Linear Regression	 6.43504	     0.007072	6.554409	 0.002301

1	Random Forest	    6.343015	  0.021272	6.51103	 0.008904

* I created a scatterplot for the linear regression model and it backed up the results that I calculated as it didn't show a linear relationship betweeen the observed position at finish and predicted position at finish

[Scatterplot](https://github.com/yeahAaron/KaggleProject/assets/112126602/ced1ff75-e52f-42ee-94e6-f759bdf97d58)

**Logistic regression model:**
* I calculated the accuracy of the model which turned out to be about 13.2%
* I also attempted to create a ranking system of the horses for the position at finish, but it ranked every single horse from 1 to the end of the dataframe !

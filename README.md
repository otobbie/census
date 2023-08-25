# Census Report
The purpose/aim of this report is to analyse the census of a modest town and the analysis used to recommend possible investment and developmental ideas for an unused plot of land in the community. The first part of this report is focused on cleaning the data, which is the first step to providing recommendations that will help with decision making, this is done by correcting error and dealing with missing records that might be encountered. 

Subsequent sections will be talking about the analysis done to give insight to the recommendations given. This includes but not limited to, an analysis of the town’s populations at hand, possible growth/ decline of the population in the coming future by first looking at the birth rate, commuters, student, employed/ retired citizens trends. 

# Data Cleaning 
Data cleaning was done on the census report to evaluate and correct possible errors which might affect the overall analysis. A backup of the original file was made, and the cleaning steps documented in case any step needs to be repeated. 

The data filled in for the ‘age’ column was not all in the same format this was corrected to put all ages to be in the integer format (e.g., 84.77995285 changes to 84, 89.77995285 changes to 89). The column ‘Age’ has a space as one of the ages, this was converted to the string ‘0’ so that the format change above can be successful. This column doesn’t have any Null, NA or NAN Values so once all the data for this column are in the same format, we move to the next cleaning phase. 

Spaces was trimmed from each column of the data to allow for easy replacement or removal. The ‘Relationship to Head of House’ column had 2 of these empty string values, one which was the ‘Clark’ family, they are 3 in the family, the head which is a female, the daughter and a male whose relationship to the head was left blank. Both adults were 38 and 40 respectively and were both married, hence the space for the male Clark was converted to ‘Husband’. While the second empty value was converted to ‘None’ since she was single and was the only occupant in the building according to the data. The 3 empty ‘Occupation’ were converted to ‘Student’ after getting the mode of the ‘Occupation’ column. The empty ‘Infirmity’ column was converted to ‘None’ after checking the mode of the column. The empty ‘First name’ column was left blank because the information could not be gotten from the data of other members of the household. 

The data was checked for null values, and it was found out just two columns had ‘nan’ values: ‘Marital Status’ and ‘Religion’. 

The NAN values for marital status where converted to single as the data showed that these comprised mostly of students who were not up to the age of 18, although it is possible to be married from the age of 16 with parental consent ​(Citizens Advice, 2019)​, the sample size of citizens that were 16 and above and had ‘nan’ values for their marital status was small and so were still converted to single. ‘M’, ‘D’, ‘S’ and ‘W’ was converted to ‘Married’, ‘Divorced’, ‘Single’ and ‘Widowed’ respectively to keep the same format. 

 

The following religions were converted to ‘None’ due insignificant number of entries (i.e., 1 or 2 entries) found: ‘Bahai’, ‘Undecided’, ‘Quaker’, ‘Sith’, ‘Jedi’, ‘Buddist’, ‘Nope’.	Especially “Jedi” because it was ruled out as a religion as it did not “promote moral or ethical improvement”​ (BBC, 2016)​. 

 

‘female’, ‘f’ and ‘F’ was converted to ‘Female’, while ‘male’, ‘m’ and ‘M’ was converted to ‘Male’ to maintain uniformity in the gender column. 

 

There was the presence of an unknown column, this was removed as its content were just the indexes of each row. Also, the ‘House Number’ Column had a value ‘Nine’, this was converted to the integer 9 and the format of the feature was changes from object to int to keep the same format across all rows of the feature (i.e., to maintain uniformity). 

 

Possible outliers were noticed for one record where a couple with a matching age of 115 was noticed and removed. Also, seven (7) records of citizens younger than 20 were noticed to be widowed which could be seen as an outlier but was left since it is possible to be widowed as such a young age. The distribution can be seen the plot below:

![Box plot distribution](https://github.com/otobbie/census/blob/main/images/img1.png?raw=true)

Another possible outlier that was spotted were citizens above the age 65 that were identified as ‘Unemployed’. These were converted to ‘Retired’ because although there is no longer a retirement age, there is a pension age and the average retirement age in the UK is 64.7 years old for men, while women leave work at an average of 63.6 years old ​(Bromley, 2022)​. These ages wouldn’t be eligible for work. This can be seen in the plot below:

![Age distribution](https://github.com/otobbie/census/blob/main/images/img2.png?raw=true)

# Population Distribution / Data Visualization 

Data Visualization follows once the data has been cleaned for error and possible outliers. The data set will have the following structure after cleaning has been completed. 

![Dataset info](https://github.com/otobbie/census/blob/main/images/img3.png?raw=true)

 The following features were added to the dataset to aid in the data visualization that was carried out: 
* Age Band: The ages of citizens calculated and inputted into a 5-year band to aid the population pyramid diagram. 

* Simplified Occupation : These include occupations which have been re-categorized into simpler occupations to allow for analysis. The simple occupations include : Unemployed, Employed, Retired, Child, Student, University Student, PhD Student. 

* Household Number: This is a count of the number of occupants of a household.

# Population Pyramid

Analysing the population pyramid below, we can see the population consist more of the youths and middle-aged adults compared to the senior citizens on the town. This suggests a ​high birth rate ​(Citizens Advice, 2019).

![population pyramid](https://github.com/otobbie/census/blob/main/images/img4.png?raw=true)

Analysing the data further we can see that a little above half of the town’s occupants are mostly employed with a percentage of 53%, alongside the students (children) taking a percentage of 23% of the total population. There is a low unemployment rate of 6%. The town has more females compared to males, with 61% being single and 26% married. A high number of the population are do not have a religion, while 22% are Christians and 11% Catholic, this means the town is comprised more of non-religious citizens. The town can be seen as a strong town as the number of infirmities in the town are below 1%:  

![sweetviz](https://github.com/otobbie/census/blob/main/images/img5.png?raw=true)

![sweetviz](https://github.com/otobbie/census/blob/main/images/img6.png?raw=true)

![sweetviz](https://github.com/otobbie/census/blob/main/images/img7.png?raw=true)

![sweetviz](https://github.com/otobbie/census/blob/main/images/img8.png?raw=true)

![sweetviz](https://github.com/otobbie/census/blob/main/images/img9.png?raw=true)

# Divorce and Marriage 

![histplot](https://github.com/otobbie/census/blob/main/images/img10.png?raw=true)

We can see from the analysis after the population pyramid regarding the ‘Gender’, that there is generally more ‘Female’ than ‘Male’ in the town. From the plot above we can see that there are more ‘Female’ divorcees than ‘Male’, which could imply that the ‘Male’ possibly leaves the town or die.  

# Religious Affiliations 

![histplot](https://github.com/otobbie/census/blob/main/images/img11.png?raw=true)

The town is mostly occupied by non-religious citizens. Looking at the plot above you can see that there is no real religion that is growing rather all the religions seems to be shrinking down the age band. Hence there is no need for a religious structure (e.g., a mosque or a church). 

# Occupancy Level 

Calculating the number of occupants per household and making a plot from it we can see that there are households with occupancies ranging from 5 – 22, which is above the median of the household number of 4 that was used as a marker to know when a household is over occupied or not. Looking at these it suggests that the current housing is being overused. We can also spot that there is high an occupancy rate for households that house lodgers and visitors which can also suggest high number of immigrants. See plot below: 

![Box plot](https://github.com/otobbie/census/blob/main/images/img12.png?raw=true)

![dataset desciption](https://github.com/otobbie/census/blob/main/images/img13.png?raw=true)

# Birth Rate 

Calculating the birth rate, we take the total count of the population and divide it from the number of births for the year and multiply it by 1,000 to give us the birth rate per every 1,000. This can be seen in the formula below: 

((Number of births in a year)/(Total number of population))*1000

Using the formula above the calculation was done for the town to give 11 births per thousand. This can be shown in the image below: 

![jupyter](https://github.com/otobbie/census/blob/main/images/img14.png?raw=true)

# Commuters 

The commuters can be identified below: 

* University students (including PhD students): There is no university in the town but rather in close by cities. Hence these set will need to commute to their various schools. 

* Employed Lodgers: These are people whose occupations take them to various locations and need a place to stay in town for the time being while they work. 

* Visitors: These are people who came to visit family or friends. 

* Putting all these variables in mind and calculating the percentage to the total population, the commuters account for 10.4% of the total population which is a high number. 

 

# Recommendations 

Due to the high number of commuters in the town there is a need to build a train station, also by looking at the occupancy level we can see that the houses are overused and hence the need to also build low density housing. Although, building a train station will only encourage the commuters and put more pressure on the houses. Hence, the low-density housing would be preferable so that the commuters have more options.  

Building other options like a religious building (a church or a mosque) would not be needed as the most part of the population with a percentage of 59% are not religious people. Also, an emergency medical building would not be advised as there are low number of infirmities in the town. 

Also due to the high number of children students, the birth rate and the number of commuters present in the town, it is advisable to invest in schooling. The commuters might bring their kids to the town, and this will make sure kids are getting good quality education. 

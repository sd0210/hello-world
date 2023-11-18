#Task: Write the function to get a dataset from Base R: Titanic
#and give the dataframe a new name of your choice
#(hint: you will want your data to be a dataframe. Use the function: as.data.frame(Titanic))
as.data.frame(Titanic)

#See the top rows of the data
#TASK: Write the function to see the top rows of the data
head(data.frame(Titanic))

#Install and call the package dplyr
#TASK: Write the functions to install and call dplyr
library(dplyr)

#Let's just see the Survived and Sex columns
#Task: Write the function to 'select' the Survived and Sex columns 
#(hint: use the 'select' function)
data.frame(Titanic)%>%select(sex,survivded)

#Let's name the dataset with just the two columns, Survived and Sex
#TASK: Write the function to save the two columns as one new dataset
#and give it a name
select_sex_survivded <- select(data.frame(Titanic), Sex, Survived)
head(select_sex_survivded)

#Let's get rid of the Sex column in the new dataset created above
#TASK: Write the function that deselects the sex column
#(hint: use the 'select' function to not select a -column)
select_survivded <- select(select_sex_survivded, -Sex)
head(select_survivded)

#Let's rename a column name
#TASK: Write the function that renames 'Sex' to 'Gender'
rename(data.frame(Titanic), Gender = Sex )

#Let's make a new dataframe with the new column name
#TASK: Write the function that names a new dataset that includes the 'gender' 
new_data.frame<- data.frame(Titanic)
new_data.frame$gender <-new_data.frame$Sex
head(new_data.frame)

#Let's 'filter' just the males from our dataset
#TASK: Write the function that includes only rows that are 'male'
new_data.frame_male<- filter(new_data.frame, Sex == "Male")
head(new_data.frame_male)

#Let's 'arrange' our data by gender (not the data you just filtered)
#TASK: Write the function to group the data by gender (hint: arrange())
new_data_arange <- arrange(new_data.frame, gender)
head(new_data_arange)

#Let's see how many people were examined in the dataset (total the frequency in the original dataframe)
#TASK: Sum the Freq column
#TASK: After you run it, write the total here:2201
examined <- sum(new_data_arange$Freq)
print(examined)

#Since we have a males dataset, let's make a females dataset
#TASK: Write the function that includes only rows that are 'female'
new_data_females <- filter(new_data.frame, Sex == "Female")
head(new_data_females)

#And now let's join the males and females
#TASK: Write the function that joins the male and female rows 
#(hint: try using 'union' or 'bind_rows')
new_male_female <- union(new_data.frame_male, new_data_females)
head(new_male_female)
tail(new_male_female)

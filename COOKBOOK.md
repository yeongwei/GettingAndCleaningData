# Introduction
This section shall illustrate the important variables and the overview procedure to generate the output file.

# Variables
1. `features` - *data.frame* that stores the information from `features.txt`
2. `activityLabels` - *data.frame* that stores the information from `activity_labels.txt`
3. `subjectFile` - Template that represents the `subject_#PREFIX#.txt` file
4. `xFile` - Template that represents the `X_#PREFIX#.txt` file
5. `yFile` - Template that represents the `y_#PREFIX#.txt` file
6. `TEST_DATA` - *data.frame* that stores data from the directory `test`
7. `TRAIN_DATA` - *data.frame* that stores data from the directory `train`
8. `UNION_DATA` - *data.frame* that store the combined data of `TEST_DATA` and `TRAIN_DATA`
9. `SUBSET_DATA` - *data.frame* that stores the *mean* and *standard deviated* nature data from `UNION_DATA`
10. `AGGREGATED_DATA` - *data.frame* that stores the *mean* aggregated data grouped by *SubjectId* and *Activity* based on `UNION_DATA`

# Procedure(s)
## Step 1
Prepare all constants into variables that would be used throughout the script.
## Step 2
Parse the `features.txt` and `activity_labels.txt` into variables to be used later.
## Step 3
Read `subjectFile`, `yFile`, `xFile` into a single *data.frame*, starting with the `#PREFIX#` as *test* then followed by *train* into `TEST_DATA` and `TRAIN_DATA` respectively.
## Step 4 <small>(Merges the training and the test sets to create one data set)</small>
Union the `TEST_DATA` and `TRAIN_DATA` as `UNION_DATA`.
## Step 5 <small>(Extracts only the measurements on the mean and standard deviation for each measurement)</small>
Get data from `UNION_DATA` by matching the column with *mean()* or *std()* and store data into `SUBSET_DATA`.
## Step 6 <small>(Uses descriptive activity names to name the activities in the data set)</small>
Set `Activity` column in `UNION_DATA` with appropriate name
## Step 7 <small>(Appropriately labels the data set with descriptive variable names)</small>
Consolidate column names and strip of unnecessary punctuations then rename column names of `UNION_DATA`.
## Step 8 <small>(From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject)</small>
Aggregate `UNION_DATA` with *mean* and store the new data into `AGGREGATED_DATA`
## Step 9 
Write `AGGREGATED_DATA` into a file with format `tidyData%Y-%m-%d.%H-%M-%S.txt`.



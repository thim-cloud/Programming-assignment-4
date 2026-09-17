# ECE 2112 - EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION

HUIT, THIMOTY JOSHUA O.

2ECE-B

9/17/2026

## Objective of this Activity

The objective of this activity is to learn how to use Pandas for data
wrangling, calculate averages, filter specific records, group data by
categories, and create visualizations using Matplotlib.

## A. VISAYAS COMMUNICATION DATAFRAME

First, the `board2.xlsx` file was loaded into a Pandas DataFrame named
`df`.


    import pandas as pd
    df = pd.read_excel("board2.xlsx")
    df


The `pd.read_excel()` function is used to read the data from the Excel
file and store it in the DataFrame named `df`.

**Checking the Column Names and Shape**

The column names and shape of the DataFrame are checked to understand
the dataset.

    columns = df.columns.tolist()
    columns

    df.shape


The `.columns` function gets the column names while `.shape` shows the
number of rows and columns in the DataFrame.

**Calculating the Average**

The subject columns used for the average are `Math`, `GEAS`,
`Electronics`, and `Communication`.


    score_columns = ["Math", "GEAS", "Electronics", "Communication"]
    df["Average"] = df[score_columns].mean(axis=1)


The `.mean(axis=1)` function calculates the average of the selected
subjects for each student.

**Selecting Visayas Communication Students**


    vis_comm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")]
    vis_comm


The condition selects students whose hometown is `Visayas` and whose
track is `Communication`.

The required columns are then stored in `VisComm`.


    VisComm = vis_comm[["Name", "Gender", "Math", "Electronics", "Average"]]
    VisComm


## B. VISAYAS FEMALE DATAFRAME

For this part, the data is filtered to find female students whose
hometown is `Visayas`.


    vis_female = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")]
    vis_female


The required columns are selected and stored in `VisFemale`.


    VisFemale = vis_female[["Name", "Track", "GEAS", "Electronics", "Average"]]
    VisFemale


Students with an average of 60 or higher are then selected.


    VisFemale[VisFemale["Average"] >= 60]


This condition displays only the students whose average is greater than
or equal to 60.

## C. CATEGORY-AVERAGE VISUALIZATION

For this part, the mean average is calculated according to three
categories: Track, Gender, and Hometown.

**Mean Average by Track**


    track_mean = df.groupby("Track")["Average"].mean()
    track_mean


The `groupby()` function groups the students according to their track,
and `.mean()` calculates the mean average for each track.

A bar graph is then created to visualize the results.

**Mean Average by Gender**


    gender_mean = df.groupby("Gender")["Average"].mean()
    gender_mean


The data is grouped according to gender and the mean average for each
gender is calculated.

A bar graph is created to show the results.

**Mean Average by Hometown**


    hometown_mean = df.groupby("Hometown")["Average"].mean()
    hometown_mean


The data is grouped according to hometown and the mean average for each
hometown is calculated.

A bar graph is created to visualize the results.

## INTERPRETATION

The `idxmax()` function is used to identify the category with the
highest sample mean for Track, Gender, and Hometown.


    highest_track = track_mean.idxmax()
    highest_gender = gender_mean.idxmax()
    highest_hometown = hometown_mean.idxmax()

The category with the highest sample mean for Track is Communication.
The category with the highest sample mean for Gender is Male.
The category with the highest sample mean for Hometown is Luzon.

## Conclusion

In this activity, I learned how to use Pandas for data wrangling and
Matplotlib for data visualization. I calculated student averages,
filtered specific groups of students, grouped data by Track, Gender, and
Hometown, and created bar graphs to compare their mean averages. I also
used `idxmax()` to identify the category with the highest sample mean.

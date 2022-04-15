# Pandas-Challenge: PyCitySchools
The Python module Pandas was used to analyze district-wide [school](../blob/main/Resources/schools_complete.csv) and [standardized test data](../blob/main/Resources/students_complete.csv). Information provided includes students' math and reading scores and school metrics. All analyses were run and saved as DataFrames in the file [schools.ipynb](../blob/main/PyCitySchools/schools.ipynb). 

## Analyses
### District Summary
The school and standardized test datasets were merged together on matching columns 'school_name'. This action appended the corresponding school's data onto appropriate rows of student information. 

A DataFrame was created on the district level, including: the total number of schools, total number of students, total budget, average math score, average reading score, percentage of students passing math, percentage of students passing reading, and the overall passing rate. 

70% or higher is necessary for the students to be passing, and overall passing staus requires a 70% or higher in both math **and** reading. 

### School Summary
A DataFrame was created on the school level, displaying: the school type, total number of students, total school budget, per student budget, average math score, average reading score, percentage of students passing math, percentage of students passing reading, and the overall passing rate. The corresponding school names were used as index values. Values were calculated with the help of Pandas' GroupBy function, allowing for each school's data to be accessed in separate DataFrames. 

### Highest Performing Schools
A DataFrame was created by sorting the School Summary DataFrame's column '% Overall Passing' in a descending fashion. Only the top 5 performing schools were displayed. 

### Lowest Performing Schools
A DataFrame was created by sorting the School Summary DataFrame's column '% Overall Passing' in an ascending fashion. Only the lowest 5 performing schools were displayed. 

### Math Scores by Grade
A DataFrame was created using the GroupBy function on the combined dataset only where the condition of a specific grade was met, returning the average of the 'math_score' column. For example, the average 9th grade math scores per school were obtained by taking a GroupBy (separating the dataset by school) only where the 'grade' column displayed '9th'. From this reduced data, the average of was taken of the 'math_score' column. This process was repeated for the remaining grades. 

The resulting DataFrame displays the calculated average math scores, with the 4 different grades as columns and school names as rows. 

### Reading Scores by Grade
A DataFrame was created using the GroupBy function on the combined dataset only where the condition of a specific grade was met, returning the average of the 'reading_score' column. For example, the average 10th grade reading scores per school were obtained by taking a GroupBy (separating the dataset by school) only where the 'grade' column displayed '10th'. From this reduced data, the average of was taken of the 'reading_score' column. This process was repeated for the remaining grades.

The resulting DataFrame displays the calculated average reading scores, with the 4 different grades as columns and the school names as rows.

### Scores by School Spending
Schools were labeled based on spending ranges per student as either '<$585', '$585-630', '$630-645', and '$645-680'. These labels were appended to the School Summary DataFrame conditionally dependent on the 'Per Student Budget' column using Panda's Cut function. 

A DataFrame was created using the GroupBy function on the newly-updated School Summary DataFrame, sorting DataFrames by 'Spending Ranges (Per Student)', to display the average math score, average reading score, average percentage of students passing math, average percentage of students passing reading, and average overall passing rate. The resulting DataFrame's rows represent the Spending Ranges.

### Scores by School Size
Schools were labeled based on school size as either 'Small (<1000)', 'Medium (1000-2000)', and 'Large (2000-5000)'. These labels were appended to the School Summary DataFrame conditionally dependent on the 'Total Students' column using Panda's Cut function. 

A DataFrame was created using the GroupBy function on the newly-updated School Summary DataFrame, sorting DataFrames by 'School Size', to display the average math score, average reading score, average percentage of students passing math, average percentage of students passing reading, and average overall passing rate. The resulting DataFrame's rows represent the School Sizes.

### Scores by School Type
A DataFrame was created using the GroupBy function on the School Summary DataFrame, separating it into DataFrames for each school type (Charter or District). With the GroupBy object, the following were calculated: average math score, average reading score, average percentage of students passing math, average percentage of students passing reading, and average overall passing rate. 

The resulting DataFrame displays the calculated metrics as columns and school types as rows. 

## Conclusions
The most startling difference in test scores (math and overall) occurs between Charter and District type schools. While their average math and reading scores both differ by less than 10 points, there is a large discrepancy between the percentage of students who pass math and pass overall between the two school types. Overall, just above half (53.67%) of the students at a District school pass both math and reading, contrasting the 90.43% who pass at a Charter school.

There also appears to be a correlation between school size and a decreasing overall passing rate, however the correlation is not linear. Both small schools (less than 1000 students) and medium schools (1000-2000 students) have around a 90% overall passing rate - 89.88% and 90.62%, respectively. As the school size increases to over 2000, the overall passing rate drops to 58.29%. Fewer resources available to a large school density can be attributed to this drop. This trend is depicted in the Bottom Performing Schools table, which shows that the bottom 5 performing schools all have greater than 2000 students.

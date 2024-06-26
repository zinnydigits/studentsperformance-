# Student Performance Analysis

## Table of Contents

- [Dataset Description](#dataset-description)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Key Findings](#key-findings)
- [Usage](#usage)
- [Dependencies](#dependencies)
- [Results](#results)

## Dataset Description

The dataset consists of 1000 entries with the following columns:

- `gender`: Male or Female
- `race/ethnicity`: Group A, B, C, D, or E
- `parental level of education`: Various levels of education
- `lunch`: Standard or free/reduced
- `test preparation course`: Completed or none
- `math score`: Scores in mathematics
- `writing score`: Scores in writing
- `reading score`: Scores in reading
- `average score`: The average of math, writing, and reading scores
- `class position`: The position in class based on average score

## Code Snippet
```python
grouped = df_students.groupby(['parental level of education', 'lunch']).size().unstack()
grouped['total'] = grouped.sum(axis = 1)
grouped['standard_perc'] = round((grouped['standard']/grouped['total'] * 100), 0)
grouped = grouped.sort_values('standard_perc')

# visualize percentage of parental group who can afford standard meal
plt.figure(figsize=(6,2.5))
grouped['standard_perc'].plot(kind='barh', color=['red', 'yellow', 'orange', 'skyblue', 'pink','purple'])
plt.ylabel('')
plt.grid(True, which = 'both', linestyle = '--', linewidth = 0.2, color = 'gray')
plt.xticks([0,10,20,30,40,50,60,70,80,90,100])
plt.title('What percentage of each Parental Level of Education can afford Standard lunch?')
plt.show()
```

## Exploratory Data Analysis

The analysis was performed using Jupyter Notebook and the following Python libraries:

- **pandas**: For data manipulation and analysis
- **NumPy**: For numerical operations
- **Matplotlib**: For plotting and visualization
- **seaborn**: For statistical data visualization

## Key Findings

- **Gender Distribution**: The dataset contains 52% females and 48% males.
- **Performance by Gender**: Females lead in all subjects except for math.
- **Lunch Type**: 64% of students have a standard lunch, while the remaining 36% have a free/reduced lunch.
- **Test Preparation Course**: Only 36% of students completed the test preparation course.
- **Parental Education Impact**: Students with more educated parents performed better in class than those whose parents have a lower level of education.
- **Lunch and Parental Education**: Students whose parents have a lower level of education ensure their kids have a standard lunch, while students whose parents have a master's degree are the least concerned with their kids' meals.
- **Race and Performance**: Group E is the smartest, with their best average score in math, while other groups (A-D) struggle with math.
- **Top Performers**: 
  - 90% of the top 10 students have a standard lunch.
  - 80% of the top 10 students are females.
  - Most top students belong to ethnic groups D and E.
- **Lowest Performers**: 
  - 70% of the bottom 10 students have a free/reduced lunch.
  - 60% of the bottom 10 students are females.
  - No students from ethnic group D are among the bottom 10.

## Usage

To replicate the analysis or use the dataset, clone the repository and run the Jupyter Notebook:

```bash
git clone https://github.com/zinnydigits/studentsperformance.git
cd student_performance
jupyter notebook
```

## Dependencies

The following Python libraries are required:

- pandas
- NumPy
- Matplotlib
- seaborn

You can install the dependencies using pip:

```bash
pip install pandas numpy matplotlib seaborn
```

## Results

The results of the analysis are presented in the Jupyter Notebook https://github.com/zinnydigits/studentsperformance-/blob/main/students_performance.html`. It includes detailed visualizations and insights derived from the dataset.

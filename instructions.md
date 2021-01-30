# Raw Data Munging

## Overview
In this assignment, you will try to make usable a real data source: **NASA's historic measurements of the Earth's surface temperatures**.  In order to do analysis of this data, some preparation work is necessary.  In particular, you will:
1. Download raw data.
1. Write a Python program to clean up (i.e. munge) the data and save it into a standard Comma-Separated Values (CSV) format text file.
1. Write a second Python program to do some simple analysis of the data in the CSV file.
1. Answer some questions about the data.

## Instructions

### Download the data
NASA's [GISS Surface Temperature Analysis web site](https://data.giss.nasa.gov/gistemp/) gives an overview of the data set - they publish recordings in the change of the Earth's surface temperature going back to the year 1880.  
- The numbers do not represent actual temperature readings, but rather represent temperature *anomalies*.
- Their [FAQ page](https://data.giss.nasa.gov/gistemp/faq/#q101) includes some additional explanations that might be helpful.

Download [the raw data in fixed-width column format](https://data.giss.nasa.gov/gistemp/tabledata_v4/GLB.Ts+dSST.txt).
- save the raw data file into the directory named `data` in this repository.

### Look it over
Take a look at the data in the file... 
- Try to understand what is represented by each row and column.  
- Look for explanations in the site's FAQ as necessary.
- Try to spot issues that will make the data difficult to analyze with a program.

### Munge it
The raw data has some some features that make it difficult to analyze with a program. 

You must write a Python program in the file named `munge.py` to clean up the raw data and save it into a CSV-formatted file named `clean_data.csv` within the `data` directory of this repository.
- You are not allowed to use any data munging or anlysis modules such as `pandas` or `csv` for munging.  You must write the code using plain Python.

Issues your program must address:
- there are many lines at the top and bottom of the file that contain notes and not the raw data - **all lines with notes must be removed**.
- the column headings are repeated on multiple lines throughout the file - **remove all but the first line of column headings**.
- there are some blank lines in the middle of the data - **remove all blank lines**.
- there is missing data indicated with `***` - figure out how to **handle missing data so that your analyses are correct**.
- since this data is in *fixed-width column format*, there are inconsistent numbers of spaces separating the numeric values... **you optionally may want to standardize how many spaces are used as separators**.
- you are welcome to do **any additional cleanup that helps** you analyze the data in the next step.

### Analyze it
Now that you have the data in easy to parse CSV format, you will perform some aggregate statistics on the data.

Write a Python program in the file named `analyze.py` that does the following:
- opens up your cleaned up data file, `clean_data.csv` and imports it using Python's `csv` module.
- outputs the average temperature anomaly for each decade since 1880.  For example, output the average temperature anomaly for the decades:
    - 1880 to 1889
    - 1890 to 1899
    - 1900 to 1909
    - ...and so on.
- You are allowed to use the `csv` module to help parse your CSV data file in the analysis, but not `pandas` or any other data parsing or analysis module.

## Instructions

The entire workshop should be approximately 45 minutes

1.  `5-10 min`: form, introductions and roles
    *   **open the [workshop form](https://forms.gle/PFJnzQviaKkqdqfC7)**: fill this out as your progress through the workshop
        *   you must be logged in to your NYU Google account to do this
        *   each group member must submit an individual form
        *   it's ok if the answers for each group member are very similar / the same
    *   **introductions**: in alphabetical order by first name, introduce yourselves by saying your:
        *   name
        *   year
        *   major
    *   **group roles**: two group members should volunteer to fill the following roles:
        1.  "leader" / screen sharer - responsible for sharing their screen and IDE / text editor
            *   everyone else should follow along by writing code on their own editor as well
        2.  time keeper - responsible for keeping track of time; notifies group when there are only 5 minutes left
    *   **ice breakers**:
        *   everyone take turns answering this question: "What's one of your most embarrassing moments?"
            *   leader starts and chooses the next person to answer by saying that person's name
            *   that person, in turn, picks the next person to go
        *   group vote: what's the _best_ breakfast food? waffles and ice cream? ramen? something else? idk 🤷
            *   come to a consensus!
            *   **add your answer to the form**


2.  `30-35 min`: work with the data set
    1.  what do the values in the file represent?
        *   the accompanying data set documentation identifies these values are _temperature anomalies_
        *   go through the [FAQ](https://data.giss.nasa.gov/gistemp/faq/#q101) to answer: what _are_ temperature anomalies?
        *   add this answer to the workshop form
    2.  write code in [workshop_01.py (download)](workshop_01.py) to read and transform the downloaded data set
        *   use plain Python to do this (no `pandas` or `csv` module)
        *   if one person seems to be dictating all of the code…
            1.  give others a chance to contribute (take turns suggesting what to write next)
            2.  take a moment to make sure everyone understands
        *   assume that the data file is in the same directory that your program is running from
        *   remove all rows that do not include data, with the exception of a single row containing the column header names (`Year`, `Jan`, `Feb`…)
        *   remove all columns that are not a month, with the exception of the first year column
        *   convert all temperature anomalies values from 0.01 degrees Celsius to degrees Fahrenheit
            *   the formula to do this can be found within the data set
            *   format the results so that there's one decimal place (use [format](https://docs.python.org/3/library/functions.html#format) with `.1f` as the second argument)
        *   write out a new version of file, and call the file `to_f_output.txt`
            *   each row should be pipe `|` delimited
            *   there should be a single row at the top of the file that contains the header names
            *   each subsequent row should contain data
        *   the content of the new file, `to_f_output.txt` should look like this (`.`s represent additional data not shown in example output) though ⚠️ **some values may be slighty different depending on when you download the original data file**:

            <div class="language-plaintext highlighter-rouge">

            <div class="highlight">

                Year|Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec
                1880|-0.3|-0.4|-0.1|-0.3|-0.1|-0.4|-0.3|-0.2|-0.2|-0.4|-0.4|-0.3
                1881|-0.3|-0.2|0.1|0.1|0.1|-0.3|0.0|-0.0|-0.3|-0.4|-0.3|-0.1
                .
                .
                2017|1.8|2.1|2.1|1.7|1.7|1.3|1.5|1.6|1.4|1.6|1.6|1.7
                2018|1.5|1.5|1.6|1.6|1.5|1.4|1.5|1.4|1.4|1.8|1.5|1.7
                .
                . 

            </div>

            </div>

3.  `5 min`: closing
    *   fill out the remaining questions in the [submission form](https://forms.gle/PFJnzQviaKkqdqfC7):
        *   list 3 things that made extracting data from / working with the file challenging
        *   fill out feedback regarding your group work
    *   remember to submit your form!
4.  At the end of the workshop, everyone will be brought back to the main room

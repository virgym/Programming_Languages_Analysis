# Analysis of Programming Language Popularity Over Time

## Overview
This project analyzes the popularity of various programming languages over time using data sourced from Stack Overflow. By tracking the number of posts tagged with specific programming languages, we can gain insights into which languages have been trending and how their popularity has evolved.

## Data Source
The data for this analysis is obtained from [StackExchange's Data Explorer](https://data.stackexchange.com/stackoverflow/query/675441/popular-programming-languages-per-over-time-eversql-com). The query extracts posts from Stack Overflow that are tagged with specific programming languages.

### Query Used:
```sql
select dateadd(month, datediff(month, 0, q.CreationDate), 0) m, TagName, count(*)
from PostTags pt
join Posts q on q.Id=pt.PostId
join Tags t on t.Id=pt.TagId
where TagName in ('java','c','c++','python','c#','javascript','assembly','php','perl','ruby','visual basic','swift','r','object-c','scratch','go','swift','delphi')
and q.CreationDate < dateadd(month, datediff(month, 0, getdate()), 0)
group by dateadd(month, datediff(month, 0, q.CreationDate), 0), TagName
order by dateadd(month, datediff(month, 0, q.CreationDate), 0)
```

## Project Structure
The notebook is organized as follows:
1. Import Libraries: Import necessary libraries such as pandas, matplotlib, and seaborn.
2. Load Data: Load the data from a CSV file obtained from the StackExchange query.
3. Data Processing: Perform data wrangling to reshape the data for analysis.
4. Data Visualization: Generate plots to visualize the trends of programming language popularity over time.

## Installation

To run this project locally, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/virgym/Programming_Languages_Analysis.git
   ```
   
2. Create a virtual environment and activate it:
    ```bash
    python -m venv venv
    source venv/bin/activate
    ```

3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## Author
👩‍💻 Mutshinya Virginia Mudau

- GitHub: <a href='https://github.com/virgym' target='_blank'>@virgym</a>
- LinkedIn: <a href='https://www.linkedin.com/in/mutshinya-virginia-mudau-168a891b9/' target='_blank'>Mutshinya Virginia Mudau</a>

## License
<p>This project is licensed under the MIT License</p>

## Acknowledgements
Special thanks to Stack Overflow and StackExchange for providing the data used in this analysis.

# TrailLink Rentals Data Pipeline

Pandas pipeline that loads equipment rental data from three different sources, cleans it through an audited step-by-step process, and answers 20 analytical queries on rental revenue and demand.

Individual assignment for **SOEN 363: Data Systems for Software Engineers** (Concordia University, Fall 2026).

## Scenario
TrailLink Rentals rents outdoor equipment across Canadian cities. Each system exports data in a different format:

| File | Source | Contents |
|---|---|---|
| `Tables/equipment.csv` | Inventory system | Equipment catalog, daily rates, stock |
| `Tables/members.xlsx` | Membership system | Members and their cities |
| `Tables/rentals.txt` | Rental platform | Rental transactions (comma-separated) |

All records are synthetic.

## Pipeline
1. **Load**: read CSV, Excel (openpyxl) and TXT into separate DataFrames; inspect with `.head()` and `.info()`.
2. **Clean** (on copies; source files are never modified), in this order:
   missing values → exact duplicates → numeric validation → date parsing → orphan foreign keys.
   Every step reports rows removed, and primary-key uniqueness is verified at the end.
3. **Analyze**: build one joined DataFrame with `revenue = quantity × rental_days × daily_rate` and answer Q1–Q20.

## Project structure
```
traillink-rentals-data-pipeline/
├── Tables/
│   ├── equipment.csv
│   ├── members.xlsx
│   └── rentals.txt
├── SOEN363_Assignment2_StudentID.ipynb
├── .gitignore
└── README.md
```

## Run it
```powershell
pip install pandas openpyxl ipykernel
```
Open the notebook in VS Code or Jupyter and choose **Run All**. Paths are relative, so run it from the repo root.

## Tech
Python 3, Pandas, openpyxl, Jupyter

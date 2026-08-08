# Swiggy Sales Dashboard 📊

An interactive Excel dashboard analyzing food-delivery sales performance — built on transaction-level order data with dynamic slicers, KPI cards, and multi-dimensional trend analysis.

![Swiggy Sales Dashboard](Screenshot%202026-08-08%20201106.png)

---

## Overview

This project turns raw, row-level food-delivery order data into a single-page interactive dashboard for exploring sales performance across time, geography, restaurants, and food categories. It's designed to be opened directly in Excel — no external BI tool required — and filtered live using built-in slicers.

**Purpose:** Give a fast, visual read on overall sales health (revenue, order volume, ratings) and let a user drill into *where* and *when* performance shifts, without writing a single formula themselves.

## Key Metrics

| Metric | Value |
|---|---|
| Total Sales | ₹53.01M |
| Average Rating | 4.34 |
| Avg Order Value | ₹268.51 |
| Rating Count | 5.59M |
| Total Orders | 197.43K |

Additional views: monthly/daily/weekly sales trends, sales by food type (Veg vs Non-Veg), sales by car... *(N/A — food category, not automotive)*, top 5 cities by sales, quarterly sales/rating/orders summary, and a state-wise sales heat map of India.

## Features

- 📌 **KPI summary strip** — Total Sales, Average Rating, Avg Order Value, Rating Count, Total Orders at a glance
- 📈 **Trend analysis** — monthly, daily, and weekly sales trend charts
- 🍽️ **Category breakdown** — Veg vs Non-Veg sales split (donut chart)
- 🗺️ **Geographic view** — state-wise sales heat map + top 5 cities by sales
- 📅 **Quarterly rollup table** — Sales, Rating, and Orders by quarter
- 🎛️ **Dynamic slicers** — filter live by Category, Month, and Restaurant Name
- 🎨 **Themed layout** — consistent Swiggy-branded color palette and iconography

## Data Sources

The dashboard is built on a single transactional dataset (`Swiggy Data` sheet) with ~197K order-level rows, including:

`State`, `City`, `Order Date`, `Day`, `Quarter`, `Week`, `Restaurant Name`, `Location`, `Category`, `Dish Name`, `Food Table (Veg/Non-Veg)`, `Price (INR)`, `Rating`, `Rating Count`

All dashboard visuals are derived from this raw table via Excel's Data Model (Power Pivot) and Power Query transformations — there is no external database or API dependency.

> **Note:** This is a sample/demo dataset used for portfolio and learning purposes. No real customer, restaurant, or transaction data is included.

## Dependencies / Tools Required

| Tool | Required | Notes |
|---|---|---|
| Microsoft Excel (Desktop) | ✅ Required | Excel 2016+ or Microsoft 365 recommended (for Power Query / Power Pivot / slicer support) |
| Power Query | ✅ Built into Excel | Used for data cleaning/shaping — no separate install needed |
| Power Pivot | ✅ Built into Excel | May need to be enabled via *File → Options → Add-ins → COM Add-ins → Power Pivot* |
| Excel for Mac / Excel Online / Google Sheets | ⚠️ Partial support | Slicers and some chart types may render or behave differently; full interactivity is only guaranteed in Excel Desktop (Windows) |
| Power BI Desktop | ❌ Not required | This is an Excel-native dashboard, not a `.pbix` file |

## Repo Structure

```
swiggy-sales-dashboard/
├── README.md                     # this file
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── data/
│   └── Swiggy_Raw_Data.xlsx      # raw source data (place your file here — see note below)
├── images/
│   └── dashboard_screenshot.png  # dashboard preview image used in this README
└── docs/
    └── data-dictionary.md        # column-level definitions for the raw dataset
```

> **File size note:** The raw data workbook is large (~20+ MB) because it contains ~197K transactional rows. GitHub's default file-size limit is 100 MB, but if your dataset grows, consider using [Git LFS](https://git-lfs.com/) for files in `data/`, or exclude the raw file from version control entirely and document how to regenerate/source it instead.

## Setup / Run Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/swiggy-sales-dashboard.git
   cd swiggy-sales-dashboard
   ```
2. **Open the workbook** — locate the `.xlsx` file in `data/` and open it in Excel Desktop.
3. **Enable content** if prompted (macros are not required for this dashboard, but Excel may prompt for external data connections — choose "Enable").
4. **Refresh the data model** (optional): `Data` tab → `Refresh All`, if you've updated the raw `Swiggy Data` sheet and want the dashboard to recalculate.
5. **Navigate to the `Dashboard` sheet tab** at the bottom of the workbook.
6. **Interact with slicers** on the left panel — Category, Months, Restaurant Name — to filter all visuals simultaneously.

### Updating the screenshot
If you modify the dashboard, export a fresh image and replace the placeholder:
1. Select the dashboard sheet range in Excel.
2. Copy as picture (`Home → Copy → Copy as Picture`) or take a screenshot.
3. Save it as `images/dashboard_screenshot.png`, overwriting the existing file.
4. Commit the change: `git add images/dashboard_screenshot.png && git commit -m "Update dashboard screenshot"`.

## Usage Tips

- Use the **Category** slicer to isolate performance for a specific cuisine or dish type before comparing cities or states.
- The **Weekly Sales Trend** chart (36 weeks) is best read alongside the **Monthly Sales Trend** for spotting short-term spikes that don't show up in monthly aggregates.
- Click multiple slicer items (Ctrl+Click in Excel) to compare combined segments rather than filtering to a single value.
- The **state-wise map** uses Excel's built-in 3D Maps / geography data types — an internet connection is required the first time it renders map shading.

## Limitations

- Sample dataset only — figures do not reflect real Swiggy business performance.
- Map visualization depends on Excel's built-in geographic data services (via Bing/TomTom, per the in-sheet attribution) and requires an internet connection on first load.
- Slicer-driven interactivity is fully supported only in Excel Desktop; behavior may vary in Excel Online, Excel for Mac, or when opened in Google Sheets.
- The workbook is not optimized for very large datasets beyond the current ~197K-row scale — further growth may require moving the data model to Power BI or a proper database backend.



## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

**Attribution:**
- Map data: © GeoNames, Microsoft, TomTom (via Excel's built-in mapping feature)
- Dashboard design/build: [Your Name]



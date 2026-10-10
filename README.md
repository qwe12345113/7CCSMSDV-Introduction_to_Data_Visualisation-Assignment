# Olympics and Paralympics Data Visualisation

An interactive, browser-based visualisation project exploring historical Olympic and Paralympic performance, participation, medal efficiency, and differences between the Summer and Winter Games.

The website brings multiple charts together on a homepage. Users can open individual visualisations and interactively filter countries, editions, seasons, and performance measures.

You can explore the interactive visualisations on my assignment homepage [here](https://qwe12345113.github.io/7CCSMSDV-Introduction_to_Data_Visualisation-Assignment/).

## Project objectives

The visualisations investigate three main questions:

1. **Team performance over time:** How does national team performance change across Games editions, and are there detectable trends?
2. **Olympics versus Paralympics:** How do the long-term performance trends of national teams differ between the two event systems?
3. **Participation and efficiency:** How is team performance associated with participation size and medal efficiency over time?

Additional charts examine the growth in participating and medal-winning countries, event counts, and average medal efficiency.

## Data sources and processing

**Data sources:** Olympic medals, Olympic hosts, Summer Paralympics, and Winter Paralympics datasets.

**Processing:** Olympic medal records were merged with host metadata and aggregated to country–year–season level. Weighted medal scores and efficiency measures were derived for analysis.

The visualisations use the following CSV files:

- `olympic_results_in_winter_paralympics_format_with_mixed.csv`
- `summer_paralympics.csv`
- `winter_paralympics.csv`

Some charts expect fields including `Country`, `Year`, `Gold`, `Silver`, `Bronze`, `M_Total`, and `P_Total`. The Olympic data also uses host information to identify Summer and Winter editions.

### Derived indicators

| Indicator | Definition |
| --- | --- |
| Total medals | `M_Total` |
| Weighted medal score | `3 × Gold + 2 × Silver + Bronze` |
| Medal efficiency | `M_Total / P_Total` |
| Weighted efficiency | `(3 × Gold + 2 × Silver + Bronze) / P_Total` |

Efficiency measures require a positive participant count (`P_Total > 0`).

## Visualisations

| Visualisation | Main purpose |
| --- | --- |
| **Olympic Medal Trends** | Compare national medal counts over time by medal type and Games season. |
| **Paralympic Medal Trends** | Explore country-level medal trends in Summer and Winter Paralympics. |
| **Team Performance by Weighted Medal Score** | Compare national teams using a common weighted performance indicator. |
| **Olympics vs Paralympics Small Multiples** | Show two performance lines per country with a shared y-axis scale across panels. |
| **Participation Size vs Medal Efficiency** | Explore participation and efficiency using a scatter plot, variable point sizes, and a year slider. |
| **Olympics vs Paralympics Expansion Trends** | Compare trends in participating or medal-winning countries. |
| **Paralympic Scatter Plots with Trend Lines** | Explore relationships among team size, medal totals, and efficiency by season. |
| **Average Medal Efficiency** | Compare summer and winter efficiency trends over time. |

Other visualisations in the project may include event-count trends and indexed medal-growth charts.

## Technologies

- **HTML5 and CSS3** — page structure and responsive layout
- **JavaScript** — state management, filtering, and interactions
- **D3.js v7** — axes, scales, SVG drawing, tooltips, and data transformations
- **PapaParse** — CSV loading and parsing in chart pages that retain the original loading approach

Libraries are referenced through CDNs, so an internet connection may be required to load the JavaScript libraries.

## Suggested project structure

Keep the homepage and chart pages in the project root, with the CSV datasets in the directory used by the HTML source:

```text
visualization/
├── chart_homepage.html
├── team_performance_weighted_medal_score.html
├── olympics_vs_paralympics_small_multiples.html
├── participation_size_vs_medal_efficiency_scatter.html
├── olympic_medal_line_chart_auto_csv_season_filter.html
├── paralympics_medal_line_chart_auto_csv_season_filter.html
├── olympics_vs_paralympics_expansion_trends.html
├── olympic_scatter_ptotal_mtotal.html
├── paralympics_medal_efficiency_vs_performance_trendline.html
├── average_medal_efficiency_summer_winter.html
├── Datasets-20260409/
│   └── Olympics-Paralympics/
│       ├── olympic_results_in_winter_paralympics_format_with_mixed.csv
│       ├── summer_paralympics.csv
│       └── winter_paralympics.csv
└── README.md
```

<!--
This structure is illustrative: use the actual filenames of the chart versions you choose to keep. In particular, update homepage `href` links if your final pages have names such as `_papa_plus_d3_fixed.html`.
-->

<!--
## How to run

1. Download or clone the project and keep the CSV files in the expected relative paths.
2. Open `chart_homepage.html` (or the actual homepage filename) in a web browser.
3. Select a chart card to open its page.
4. Use the chart's controls to filter the displayed data.

**Important:** The existing pages use relative CSV URLs, often through `Papa.parse(..., { download: true })`. Some browser configurations block loading local CSV files when opening an HTML file directly through `file://`. If a chart stays on *Loading CSV data...* or reports a failed CSV load, check the browser console and verify the relative paths. Where local-file access is blocked, serving the same folder over HTTP is a compatibility fallback:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000/` and open the homepage. This does not require changing the CSV parsing code to `d3.csv()`.
-->

## How to use the website

The homepage provides links to the charts. Depending on the visualisation, interactive controls include:

- **Dataset:** Olympics or Paralympics
- **Games type:** Summer or Winter (and, in some charts, a combined view)
- **Country/team selection:** Search, choose multiple countries, select top teams, or clear all
- **Metric:** Medal type, total medals, weighted medal score, or efficiency
- **Year slider:** Explore individual Games editions in scatter plots
- **Tooltips:** Hover over plotted points to inspect the corresponding observations

Each chart page loads its datasets when opened. Changes to controls update its chart without requiring manual CSV file selection.

<!--
## Notes and limitations

- Country/team names are taken from the underlying datasets and may differ between Olympic and Paralympic records. Harmonisation may be necessary for exact cross-system comparisons.
- Some charts omit observations without valid participant counts when calculating efficiency.
- Small-multiple panels can share a **y-axis scale** while using individual **x-axis year ranges** for legibility. When interpreting relative timing across panels, check each panel's year labels.
- Top-team rankings depend on the selected dataset, season, and metric.
- The project relies on the supplied CSV datasets; it does not fetch up-to-date competition results automatically.

## Extending the dashboard

To add another chart:

1. Create a new HTML file using D3.js and the appropriate CSV dataset(s).
2. Add a new chart card to the homepage and point its `href` to the new HTML file.
3. Add a preview image to the card if available.
4. Update this README with the chart's purpose and controls.
-->
## Attribution

Source datasets should be credited according to their original licenses and providers. Add the dataset provenance and citation details supplied with the coursework materials before public distribution.

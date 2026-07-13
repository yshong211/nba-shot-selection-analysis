# The Evolution of Shot Selection in the NBA

How has NBA shot selection changed since 2000, and does it differ by position? Team project for the University of Michigan Master of Applied Data Science program (Milestone I, Winter 2026).

**Team:** Brady Hong, Keegan Schmit, Samantha Hastie

Full write-up with visualizations: [report.pdf](report.pdf)

## Questions

1. How has the distribution of shots in the paint, mid-range, and three-point zones changed from the early 2000s to the present?
2. How do these trends differ for guards, forwards, and centers?
3. Are the changes in shot selection accompanied by changes in shot efficiency?

## Data

- **NBA Stats API** (via `nba_api`): ~4.8M shot records across 24 seasons (2000-01 to 2023-24), with shot coordinates, shot type, and outcome
- **Basketball Reference**: player-season metadata (position, team), scraped with `pandas.read_html`

The two sources were merged on standardized player names and season. Name standardization (ASCII conversion, suffix removal, manual mapping of nicknames) and handling of multi-team player seasons brought the merge to a 99.8% match rate.

## Methods

- Shot location heatmaps comparing the early era (2000-2005) vs. the modern era (2019-2024), by position group
- Stacked bar charts of shot zone proportions by season and position
- Chi-square tests of independence (era × shot zone, overall and by position) with Cramér's V effect sizes
- Bootstrap difference-in-means tests on FG% by zone with 95% confidence intervals

## Key Findings

- Three-point attempts nearly doubled, from under 20% of shots (2000-2005) to over 38% (2019-2024), while mid-range attempts fell below 14%. Three-pointers passed mid-range shots league-wide around the 2014-15 season.
- The shift happened at every position, not just guards. Effect sizes were actually largest for forwards (V = 0.348) and centers (V = 0.353).
- Efficiency improved in every zone, but the three-point gain was the smallest. The modern rise in three-point scoring comes mainly from shot selection, not better shooting accuracy.

## Tools

Python, pandas, NumPy, SciPy, Matplotlib, Seaborn, Altair, nba_api

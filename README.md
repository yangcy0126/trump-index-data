# trump-index-data

This repository is the dedicated raw-data mirror for the Trump index pipeline.

It stores the source CSV files used to build:

- the headline Trump indices
- the country-directed Trump sentiment series

Current layout:

- `data/raw/`
  - `trump_posts_all_platforms.csv`
  - `trump_posts_all_platforms_llm.csv`
  - `twitter_archive.csv`
  - `truthsocial_archive.csv`
  - `trump_posts_llm_scores.csv`
  - `trump_posts_country_directed.csv`
  - `trump_country_directed_text_scores.csv`
- `data/metadata/`
  - `trump_index_summary_llm.json`
  - `trump_country_directed_summary.json`
  - `manifest.json`
  - `latest.json`

Update workflow:

1. Refresh and score the Trump indices in the main workspace.
2. Rebuild website Trump assets.
3. The workspace script `DSI-ICF/code/sync_trump_index_data_repo.py` mirrors the latest raw CSVs into this repository.

Notes:

- This repository is intended for raw CSV distribution and versioning.
- The public website repository should continue to keep only processed JSON and workbook assets.

The headline indices end on the last archived post, including reposts. The country-directed
panel ends on the last original text post. Both cutoff dates are in `data/metadata/latest.json`.
For Truth Social posts dated August 26, 2026 onward, quoted cards do not supply the outer
post's author, timestamp or text. Quotes without added text count as activity, not scored
rhetoric. Earlier published source records and labels are retained. The shock index is
standardized over all active days, so extending the sample can revise earlier shock readings.

# Profile README Tools

This repo uses two automation tools for the profile README.

## 1. `pemtajo/badge-readme`

- Purpose: fetch public Credly badges and write them into the badge section in `README.md`.
- Workflow: `.github/workflows/update-badges.yml`
- Trigger: manual only with `workflow_dispatch`
- Input used here:
  - `CREDLY_USER: han-li.e090ae07`
  - `NUMBER_LAST_BADGES: 0` to include all badges
- README markers:

```md
<!--START_SECTION:badges-->
<!--END_SECTION:badges-->
```

- Notes:
  - this is useful when a new certification is added
  - it does not need a schedule because badges change infrequently

## 2. `vn7n24fzkq/github-profile-summary-cards`

- Purpose: generate GitHub stats SVG files inside this repo and avoid live API rate-limit issues in the README.
- Workflow: `.github/workflows/update-summary-cards.yml`
- Trigger: weekly schedule plus manual run
- Schedule: `0 3 * * 0` (every Sunday at 03:00 UTC)
- Secret required:
  - `SUMMARY_GITHUB_TOKEN`
- Output location:
  - `profile-summary-card-output/github_dark/1-repos-per-language.svg`
  - `profile-summary-card-output/github_dark/3-stats.svg`
- README usage:
  - `README.md` references the generated SVGs from this repository instead of the public summary-cards API

## When to run which

- Run `Update Badges` after earning a new badge.
- Run `Update Summary Cards` manually any time you want a fresh stats snapshot, or let the weekly schedule handle it.

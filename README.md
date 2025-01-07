# Web Portfolio Repository

This repository contains the web portfolio, including an automated process to synchronize the `docs` directory from the [Angular Portfolio Repository](https://github.com/solo-leveler/angular-portfolio).

## Overview

- **Purpose:** Automatically sync the `docs` folder from Angular Portfolio (`repo1`) to this repository (`repo2`).
- **Automation Tool:** Uses GitHub Actions for automation.

## How It Works

1. **Trigger Events:**
   - **Push Event:** When changes are made to the `docs` directory in `repo1`.
   - **Scheduled Job:** Runs on the 17th of every month.

2. **Dispatch Workflow (in `repo1`):**
   - Detects changes in the `docs` directory.
   - Sends a repository dispatch event to `repo2`.

3. **Sync Workflow (in `repo2`):**
   - Listens for dispatch events from `repo1`.
   - Clones the `docs` directory from `repo1`.
   - Syncs the `docs` directory with `repo2`.
   - Commits and pushes any changes to `repo2`.

## Configuration

- **Secrets Used:**
  - `REPO1_DISPATCH_TOKEN` in `repo1`: Personal Access Token (PAT) for dispatching events.
  - `REPO1_URL` in `repo2`: URL of `repo1` to clone the repository.
  - `REPO2_TOKEN` in `repo2`: PAT for authentication to push changes.

## Manual Triggering

- Navigate to the **Actions** tab in `repo1`.
- Select the "Dispatch Docs Changes to Deploy Repository" workflow.
- Click "Run workflow" to manually trigger the synchronization process.

## Conclusion

This setup ensures that the documentation in `repo2` remains up-to-date with any changes made in `repo1`, both automatically and on a schedule.

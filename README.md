# Download workflow artifact GitHub Action

An action that downloads and extracts the latest uploaded artifact associated with a given workflow.

This action is based on https://github.com/dawidd6/action-download-artifact which does not work properly when the latest artifact is needed.

Let's suppose you have a workflow with a job in it that at the end uploads an artifact using `actions/upload-artifact` action and you want to download this artifact in another workflow that is run after the first one. Official `actions/download-artifact` does not allow this. That's why `dawidd6/action-download-artifact` decided to create this action. By knowing only the workflow name you can download the previously uploaded artifact from different workflow and use it.

## Usage


```yaml
- name: Download latest artifact
  uses: meawallet/action-download-artifact
  with:
    # Optional, GitHub token, a Personal Access Token with `public_repo` scope if needed
    # Required, if artifact is from a different repo
    # Required, if repo is private a Personal Access Token with `repo` scope is needed
    github_token: ${{ secrets.PAT_TOKEN }}
    # Required, defaults to current repo
    repo: owner/repository
    # Required, workflow file name or ID
    workflow: workflow_name.yml
    # Optional, directory where to extract artifact(s), defaults to current directory
    path: extract_here
```

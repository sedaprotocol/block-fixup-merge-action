# SEDA block-fixup-merge-action

Fails a pull request check when the PR contains autosquash commits whose subject
starts with `fixup!`, `squash!`, or `amend!`.

## Usage

Add a workflow like this to another repository:

```yaml
name: PR checks

on: [pull_request]

permissions:
  contents: read
  pull-requests: read

jobs:
  main:
    runs-on: ubuntu-latest

    steps:
      - name: Check autosquash commits
        uses: sedaprotocol/block-fixup-merge-action@v1
```

## How it works

The action uses the GitHub API to fetch every commit in the pull request and
checks each commit subject for `fixup!`, `squash!`, or `amend!`. If it finds
one, it lists the detected commits and fails the check; otherwise, it passes.



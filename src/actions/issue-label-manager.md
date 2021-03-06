---
path: '/issue-label-manager'
title: 'Issue Label Manager'
github_url: 'https://github.com/lannonbr/issue-label-manager-action'
author: 'lannonbr'
tags: ['github', 'labels', 'automation']
subtitle: 'This GitHub Action allows you to declaratively state the labels to be defined in a repo.'
---

In the repo you'd like to use this, define a JSON file in `.github/labels.json`. This file will contain an array of objects that have a name, color, and description as shown in the example below.

![labels.json file](https://github.com/lannonbr/issue-label-manager-action/raw/master/screenshots/json.png)

Then, set up a workflow that executes this action. When run, it will update the list of labels in the repo to match the JSON file and will delete any other labels.

The result of using the labels.json file shown above is as follows:

![Labels result](https://github.com/lannonbr/issue-label-manager-action/raw/master/screenshots/labels.png)

If a label doesn't need a description, leave out the `description` field of the entry in the json file and when deployed the label will not contain a description.

## Usage

This action only needs the GITHUB_TOKEN secret as it interacts with the GitHub API to modify labels. The action can be used as such:

```hcl
action "Update Label" {
  uses = "lannonbr/issue-label-manager-action@master"
  secrets = ["GITHUB_TOKEN"]
}
```

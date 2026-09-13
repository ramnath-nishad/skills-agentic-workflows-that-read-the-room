---
name: update-github-info
description: Keep the GitHub Info page current with useful GitHub Blog and Changelog updates.
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read

tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:

network:
  allowed:
    - defaults
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[github-info] "
---

# Update GitHub Info

Read `notes/mona-notes.md` before making any changes.

Use the web-fetch tool to read:

- https://github.blog/latest/
- https://github.blog/changelog/

Select concise, practical updates that help developers learn GitHub faster. Mention the source whenever an update comes from the GitHub Blog or GitHub Changelog. Use the GitHub repository API tools to read any repository guidance or reference files you need; do not use terminal, CLI, or sandboxed commands for that research.

Update `site/content/github-info.md` only when there is a worthwhile, accurate update. Preserve the file's existing structure and writing style, and keep the summaries short.

When changes are needed, use the edit tool to make them and request the `create-pull-request` safe output. Open a pull request for Mona to review; do not write directly to the default branch. Include a concise summary of the changes and the sources reviewed in the pull request body.
# 🧹 deadnix-action

**GitHub Action to find and remove unused Nix code** using [`deadnix`](https://github.com/astro/deadnix).

## 🚀 Features
- Automatically scans your repository for dead Nix code.
- Removes unused code and commits the changes.
- Pushes the changes or creates a pull request (optional).
- Works with [GitHub Actions](https://github.com/features/actions).

## 📥 Installation

To use this action in your GitHub repository, add it to a workflow file:

```yaml
name: Dead code analysis

on:
  workflow_dispatch:
  push:

jobs:
  deadnix:
    name: Deadnix
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@main
      - uses: DeterminateSystems/nix-installer-action@main
      - uses: phucleeuwu/deadnix-action@v3
```

## ⚙️ Inputs

| Name           | Description | Default |
|---------------|-------------|---------|
| `flags`       | Command-line flags for `deadnix` | `--edit` |
| `author`      | Commit author | `${{ github.actor }} <${{ github.actor }}@users.noreply.github.com>` |
| `committer`   | Committer name & email | `GitHub <noreply@github.com>` |
| `directory`   | Directory to scan | `.` |
| `commit_message` | Commit message | `Remove dead Nix code` |

## 🛠 Example with Pull Request Creation
If you want to create a **pull request** instead of committing directly:

```yaml
- uses: phucleeuwu/deadnix-action@v3
  with:
    open_pr: true
```

## 📝 License
This project is licensed under the MIT License.

---

Made with ❤️ by [phucleeuwu](https://github.com/phucleeuwu)

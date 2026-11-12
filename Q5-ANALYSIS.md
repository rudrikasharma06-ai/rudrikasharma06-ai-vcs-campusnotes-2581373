# Q5 - Git Hooks Implementation

## 1. Introduction
Git hooks are scripts that run automatically during specific Git events to enforce rules and maintain code quality.

## 2. Pre-commit Hook
File: .githooks/pre-commit

Purpose:
- Runs before a commit is created.
- Checks staged files for unwanted placeholder markers.
- Blocks commits when such markers are found.
- Allows commits when validation passes.

Testing:
- A staged file containing a placeholder marker was rejected.
- After removing it, the commit succeeded.

## 3. Commit-msg Hook
File: .githooks/commit-msg

Purpose:
- Runs when a commit message is prepared.
- Requires at least 10 characters.
- Accepts feat:, fix:, docs:, refactor:, and chore: prefixes.

Testing:
- A short message was rejected.
- An invalid prefix was rejected.
- A valid docs: message was accepted.

## 4. Local Hooks vs Shared Hooks

### Default .git/hooks
- Git normally stores hooks inside .git/hooks.
- This folder is local Git metadata.
- It is not tracked or shared when a repository is cloned.

### Project-level .githooks
- We created a project-level .githooks folder.
- Its scripts can be committed and pushed to GitHub.
- Collaborators can use the same scripts.

To activate shared hooks after cloning, run:

git config core.hooksPath .githooks

Each collaborator must run this configuration command locally.

## 5. Conclusion
Both hooks were implemented and tested successfully. The project-level .githooks folder allows the hook scripts to be shared through GitHub.

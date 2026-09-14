---
name: smart-commit
description: Writes clean, Conventional Commit-style messages from a git diff. Use this whenever the user is about to commit changes and wants a commit message written or improved, asks Claude to "write a commit message," "generate a commit," or is running this as part of a pre-commit hook or commit-msg workflow.
---

# Smart Commit

Turn a set of staged changes into a clear, well-formatted commit message.

## Instructions

1. Read the diff of changes provided (e.g. the output of `git diff --cached`).
2. Identify the primary type of change:
   `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `style`, `perf`, `build`, or `ci`.
3. Write the message using the Conventional Commits format:
   - Summary line: `<type>(<optional scope>): <short description>`
   - Use imperative mood ("add", "fix", "remove" — not "added", "fixed", "removed").
   - Keep the summary line under ~72 characters.
4. If the change is non-trivial, add a short body below the summary explaining *why* the change was made, not just what changed.
5. If the diff touches several unrelated areas, name the most significant change in the summary and list the rest as bullet points in the body.
6. Never invent details that aren't supported by the diff — if the intent behind a change is unclear, say so rather than guessing.

## Example
Test
Given a diff that adds retry logic to an API client:

```
feat(api-client): add exponential backoff on 5xx responses

Requests were failing outright on transient server errors. Retries
now back off exponentially (up to 3 attempts) before giving up.
```

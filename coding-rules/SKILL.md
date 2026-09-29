---
name: coding-rules
description: "Apply these personal coding conventions whenever writing, editing, generating, or reviewing code: comment discipline (default to no comments — code should read as its own explanation; only comment context the code truly cannot show, such as business-logic rationale, a past decision, a ticket number, or a non-obvious constraint, and keep any comment compact and focused), implementation-before-tests sequencing (when asked to implement or fix something, write only the logic/implementation files first, and hold off on writing or running tests until the user confirms the logic or explicitly asks for tests), and no unsolicited git actions (never commit, push, or open a PR on your own initiative — stop after making changes and let the user review first, unless they explicitly say otherwise). Consult this skill for ANY coding task — implementing a feature, fixing a bug, refactoring, or even a small edit — even if the user's request doesn't mention comments, tests, or git at all, since these rules apply by default in the background."
---

# Coding Rules

Personal conventions that apply to every coding task, by default, whether or
not the request mentions them.

## Comments

Code is the primary explanation. A comment that restates what the next line
does adds a second thing to keep in sync and rot when the code changes; the
name of the function or variable already carries that information.

Default to zero comments. Add one only when it carries information the code
itself cannot express:

- the business reason behind a rule ("why 30 days, not 7")
- a decision that was made and could look wrong in isolation (a deliberate
  tradeoff, a workaround for a specific external bug)
- a ticket/issue number tying the change to a larger context
- a non-obvious constraint or invariant a future editor could easily break

When a comment is warranted, keep it to one line, placed right next to the
code it explains. State the "why," not the "what" — skip the comment
entirely if removing it wouldn't leave a future reader confused.

## Implement first, test later

When asked to implement or fix something, write the logic/implementation
files and stop there. Do not follow up by writing or running tests in the
same pass.

The reasoning: right after a first pass, the logic is still the most likely
thing to change — the user may redirect the approach, adjust edge cases, or
ask for something different once they see it. Tests written against that
first draft are often thrown away or rewritten anyway, which wastes the
effort and can even anchor you to a wrong design.

Wait for one of two signals before writing tests:
- the user confirms the logic/behavior is correct, or
- the user explicitly asks for tests.

## No unsolicited commits, pushes, or PRs

After making changes, stop and hand control back for review. Do not run
`git commit`, `git push`, or open a pull request on your own initiative,
even if the change looks complete and correct to you.

The user needs the chance to read the diff themselves before it becomes part
of history or goes anywhere shared. Only commit, push, or open a PR when the
user explicitly asks for it for this change — a prior "yes" for a past change
doesn't carry forward to a new one.

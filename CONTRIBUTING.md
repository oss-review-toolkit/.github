# Introduction

The team behind the [OSS Review Toolkit](https://github.com/oss-review-toolkit/ort) gratefully accepts contributions via
[pull requests](https://help.github.com/articles/about-pull-requests/) filed against the
[GitHub project](https://github.com/oss-review-toolkit/ort/pulls).

# Signing off each Commit

As part of filing a pull request we ask you to sign off the
[Developer Certificate of Origin](https://developercertificate.org/) (DCO) in each commit.
Any Pull Request with commits that are not signed off will be reject by the
[DCO check](https://probot.github.io/apps/dco/).

A DCO is lightweight way for a contributor to confirm that they wrote or otherwise have the right
to submit code or documentation to a project. Simply add `Signed-off-by` as shown in the example below
to indicate that you agree with the DCO.

Example for a commit message with a sign-off:

```
    spdx-utils: Add sanity checks for values of the mapping objects

    Signed-off-by: John Doe <john.doe@oss-review-toolkit.org>
```

Git has the `-s` option (lower case) for `commit` that can sign off a commit for you, see example below:

`$ git commit -s -m 'spdx-utils: Add sanity checks for values of the mapping objects'`

## Git History

In order to maintain a high software quality standard, we strongly prefer contributions to follow these rules:

- [Ensure that your commit messages will make your mom proud](https://www.robertcooper.me/git-commit-messages) :wink:

- Each commit in a pull request should be atomic, in the sense that it passes all checks (build, static code analysis,
  tests) individually, and deals with one thing at a time while being self-contained. Do not add commits to a pull
  request that (partly) undo changes from an earlier commit in the same pull request, as that makes a reviewer's life
  harder (consider squashing diff hunks in this case).

- We pay more attention to the quality of commit messages than most other projects on GitHub do.
  In general, we share the view on how commit messages should be written with
  [the Git project itself](https://github.com/git/git/blob/master/Documentation/SubmittingPatches):

  - [Make separate commits for logically separate changes.](https://github.com/git/git/blob/e6932248fcb41fb94a0be484050881e03c7eb298/Documentation/SubmittingPatches#L43)
    For example, pure formatting changes that do not affect software behavior usually do not belong in the same commit as
    changes to program logic.
  - [Describe your changes well.](https://github.com/git/git/blob/e6932248fcb41fb94a0be484050881e03c7eb298/Documentation/SubmittingPatches#L101)
    Do not just repeat in prose what is "obvious" from the code, but provide a rationale explaining *why* you believe
    your change is necessary.
  - [Describe your changes in the imperative.](https://github.com/git/git/blob/e6932248fcb41fb94a0be484050881e03c7eb298/Documentation/SubmittingPatches#L133)
    Instead of writing "Fixes an issue with encoding" prefer "Fix an encoding issue". Think about it like the commit
    only does something *if* it is applied. This usually results in more concise commit messages.
  - [We are picky about whitespaces.](https://github.com/git/git/blob/e6932248fcb41fb94a0be484050881e03c7eb298/Documentation/SubmittingPatches#L95)
    Trailing whitespace and duplicate blank lines are simply a superfluous annoyance, and most Git tools flag them red
    in the diff anyway. We generally use four spaces for indentation in Kotlin code, and two spaces for indentation in
    JSON / YAML files.

  If you have ever wondered how a "perfect" commit message is supposed to look like, just look at basically any of
  [Jeff King's commits](https://github.com/git/git/commits?author=peff) in the Git project.

- When addressing review comments in a pull request, please fix the issue in the commit where it appears, not in a new
  commit on top of the pull request's history. While this requires force-pushing of the new iteration of your pull
  request's branch, it has several advantages:

  - Reviewers that go through (larger) pull requests commit by commit are always up-to-date with latest fixes, instead
    of coming across a commit that addresses their remarks only at the end.
  - It maintains a cleaner history without distracting commits like "Address review comments".
  - As a result, tools like [git-bisect](https://git-scm.com/docs/git-bisect) can operate in a more meaningful way.
  - Fixing up commits allows for making fixes to commit messages, which is not possible by only adding new commits.

  If you are unfamiliar with fixing up existing commits, please read about [rewriting history](https://git-scm.com/book/id/v2/Git-Tools-Rewriting-History)
  and `git rebase --interactive` in particular.

- To resolve conflicts, rebase pull request branches onto their target branch instead of merging the target branch into
  the pull request branch. This again results in a cleaner history without "criss-cross" merges.

## Coding Conventions

Here are some rules of thumb in no particular order:

- Do not use wildcard imports (with a few [exceptions](https://github.com/oss-review-toolkit/ort/blob/master/.detekt.yml)).
- Sort references (like imports, dependencies etc.) strictly alphabetically (ASCII order, i.e. capital letters first),
  with blank lines between imports from different top-level packages.
- Group code logically using blank lines, e.g. before and after code blocks enclosed by curly braces, or before return
  statements.
- Do not use blank lines directly after opening curly braces.
- Do not use duplicate blank lines.
- Use proper spelling, grammar, and punctuation in *all* documentation, code comments (incl. TODOs) and commit messages.
- Do not commit out-commented code.
- Use `println()` only in CLI modules and `log` in library modules.

We aim to have automated checks for these rules, but are bound to what [detekt](https://github.com/detekt/detekt) /
[ktlint](https://github.com/pinterest/ktlint) support. In any case, please [run the `detekt` task](./README.md#development)
locally before contributing.

## Governance

OSS Review Toolkit (ORT) is a [Linux Foundation project](https://www.linuxfoundation.org/) and part of [ACT](https://automatecompliance.org/). To learn more on how the project is governed, including its charter, see the [ort-governance](https://github.com/oss-review-toolkit/ort-governance) repository.

Thank you for reading and happy contributing!

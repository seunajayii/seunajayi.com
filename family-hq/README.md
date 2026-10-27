# Ajayi Family HQ

A shared household command board for the family: schedules, school, meals,
lists, and — the whole point — a single place where anything about to be
dropped is visible to everyone.

## What this folder is

`index.html` is the entire app. No build step, no dependencies.

It is published as a private Claude Artifact, which supplies two runtime
capabilities the page declares:

- `db` — the shared database. Every viewer sees the same live data.
- `user` — used only to tell a read-only viewer from someone who can write.

**No family data lives in this repository.** People, items, meals, lists and
the email review queue are all stored in the artifact's database, not in the
page source. This file is just the interface.

## Structure

| Collection  | Holds |
|-------------|-------|
| `people`    | Everyone on the board: parents, children, nanny, aunts |
| `items`     | The universal unit — task, appointment, school, chore, admin, event |
| `meals`     | One document per day, keyed `YYYY-MM-DD` |
| `listitems` | Grocery, household, pharmacy, school run |
| `inbox`     | Items extracted from school email, awaiting approval |

Every item carries an `owner`. An item with no owner that is due within three
days, or any item past its date, is an **open ball** and surfaces at the top of
the Today view.

## Time

All dates resolve against `Africa/Lagos`, deliberately. The household's day is
Lagos's day regardless of where any individual is reading the board from.

## Wall mode

`#wall` on the URL strips the navigation and enlarges type for an always-on
kitchen tablet.

## Changing it

Edit `index.html` and republish to the same artifact URL. Data survives
republishing.

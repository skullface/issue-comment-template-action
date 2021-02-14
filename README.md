# Issue comment template action 🚀

The GitHub Actions bot will post a new comment, following the templated content you provide, on an issue you specify, at the time you schedule.

## How does it work? 
* Runs on a [schedule via cron](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events).
* Uses the official [`github-script`](https://github.com/actions/github-script) action to leverage the GitHub API. JavaScript in your action! 

## What do I customize?

* The schedule
* The issue number
* The comment body

There are comments in the action itself to help walk you through it 💖

### [Schedule](https://github.com/skullface/issue-comment-template-action/blob/main/action.yaml#L10)

Per the [GitHub Actions docs](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events):
> You can schedule a workflow to run at specific UTC times using POSIX cron syntax. The shortest interval you can run scheduled workflows is once every 5 minutes.

Determine when you want the action to run in [24-hour format in the UTC timezone](https://time.is/compare/UTC), then use [crontab guru](https://crontab.guru/) to generate cron syntax for you (or [check out their examples](https://crontab.guru/examples.html)).

The default schedule in the action is 5:30pm UTC (9:30am PT) every Friday, which reads in cron syntax as [`30_17_*_*_FRI`](https://crontab.guru/#30_17_*_*_FRI).

```yaml
schedule:
  # Define your own schedule after "cron: "
  # Add a comment to the end of the line to read it in plain language 🕓
  # https://docs.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events
  - cron: 30 17 * * FRI # Every Friday at 5:30pm UTC / 9:30am PT
```

### [Issue number](https://github.com/skullface/issue-comment-template-action/blob/main/action.yaml#L21)
```yaml
issue_number: 420, # replace with the number for the specific issue you want to update
```

### [Comment body](https://github.com/skullface/issue-comment-template-action/blob/main/action.yaml#L24-L33)
```yaml
body: `# Replace me!

Use multi-line **markdown** here to create your own templated issue comment.

| Even | Tables | 
| --- | --- |
| Yes! | Tables! |

Just keep the comment body between the backticks.
`
```

## Why would I use this?
Any time you need to keep a specific issue regularly updated!

* Running issue for regular meeting agendas
* Reminder issue to ping you or your team to post a bi-weekly sprint summary

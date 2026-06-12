---
title: "help understanding roles of commands: at, batch and anacron"
date: 2010-11-19
forum: General Help
---

### Post by fantastic on 2010-11-19
I'm trying to understand the role of the *at* command. Does cron use *at* to run its jobs? Or is *at*, and batch for that matter, a separate cue that is only stored while the computer is on.

As for anacron, anacron on runs once a day and is geared for a computer that is turned of frequently, as opposed to a server when it is on all the time.

I've already man'ed these commands, and googled. I'm just trying to understand more how they work.

---

### Post by dcstar on 2010-11-19
> **fantastic said:**
> I'm trying to understand the role of the *at* command. Does cron use *at* to run its jobs? Or is *at*, and batch for that matter, a separate cue that is only stored while the computer is on.

As for anacron, anacron on runs once a day and is geared for a computer that is turned of frequently, as opposed to a server when it is on all the time.

I've already man'ed these commands, and googled. I'm just trying to understand more how they work.

[LIST=1]
[*]AFAIK "at" is used for running jobs at specific times, these may just be single jobs so there is no recurring entry in the crontab (for recurring cron jobs)
[*]Anacron will run cron jobs that may have been missed because the system is turned off - servers are not supposed to be turned off so they don't need anacron. Most cron jobs are there for important reasons so they should be run and not ignored because the system could not run them at the specified time - anacron achieves this requirement.
[/LIST]

---

### Post by fantastic on 2010-11-22
> **dcstar said:**
> [LIST=1]
[*]AFAIK "at" is used for running jobs at specific times, these may just be single jobs so there is no recurring entry in the crontab (for recurring cron jobs)
[*]Anacron will run cron jobs that may have been missed because the system is turned off - servers are not supposed to be turned off so they don't need anacron. Most cron jobs are there for important reasons so they should be run and not ignored because the system could not run them at the specified time - anacron achieves this requirement.
[/LIST]

Thanks.

Processed over this and now I understand.

---


---
title: "fcron job using random time"
date: 2010-09-16
forum: General Help
---

### Post by thaleia on 2010-09-16
Hey guys,

I need to write a cronjob using fcron.

The job shall run after every 4 hours in the first 30 minutes at a random time

For instance:

04.13am, 08.05am, 12.28pm, ...

It doesn't matter whether the job starts at a defined time (4am, 8am, 12pm, ...) or if it depends on the uptime of the system.

My best shot is:

@ 240 , %random 1-30 * * * * echo "hello" > echo.log

This job seems to run every 240 minutes (=4 hours) at a random time between the first thirty minutes, but it just creates an empty file called "echo.log". The echo-command is not executed.

Please help!!!

PS: Since I'm new to this forum please be patient if I picked the wrong sub-category.
PPS: Google and forum search wasn't helpfull at all :(

---


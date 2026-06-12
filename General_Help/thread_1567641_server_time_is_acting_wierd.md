---
title: "server time is acting wierd"
date: 2010-09-04
forum: General Help
---

### Post by ripken204 on 2010-09-04
so i set up a cron job and one of the things it does is creates a log file with the current date and time. the cron runs at the proper time, 2 am. the system time is correct.
what is odd is that the file creation time is an hour ahead, 3am.

if i manually create a file the creating time is the correct time.
the rsync command is creating the log file...
yet in the log file the recorded times are correct.
anyone have an idea of what's going on?

---


---
title: "Log Viewer gone wild! (Eats up all available RAM)"
date: 2010-03-26
forum: General Help
---

### Post by auh2o on 2010-03-26
Well, I can't make use of the Gnome log file viewer anymore. Seconds after I start it, it will gray out and proceed to steadily lay claim to all my available RAM. It doesn't matter which log I choose, or if I don't choose one at all. Same thing. I have 1GB RAM, and when I took the included screencap the log viewer had taken almost 80% of it. It was at 90% before I forced a shutdown of the process. Does anyone have the slightest idea what might be causing this?

---

### Post by T3kG33k on 2011-01-25
I've been fighting with the same problem too!  I'm guessing that it has something to do with the size of the log files.  This also probably has something to with logrotate not running as a cron job.  I'm trying to figure this out on my own also since sometimes I need to look at the logs and I'm not quite good enough with a CLI yet.

I'll post back here if I find anything out.

---


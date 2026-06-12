---
title: "crontab not running, what am I missing?"
date: 2011-04-23
forum: General Help
---

### Post by bleutyler on 2011-04-23
I am unsure why this crontab is not executing.

00 00 * * * /bin/cp /home/tyler/.gnome2/gnotime.d/gnotime-data.xml /home/tyler/Dropbox/timesheets/gnotime-data.xml.`date +%Y%m%d-%H%M` >> /home/tyler/.gnome2/gnotime.d/cp.cronjob.log 2>&1 

All folder exist, the job is not running at all since the final log file cp.cronjob.log is never created

What am I missing?  

it is my personal crontab, not root's. 

I even did the MAILTO="" trick, it is not working.  

Of course, running the command verbatim from the shell works perfectly.

---


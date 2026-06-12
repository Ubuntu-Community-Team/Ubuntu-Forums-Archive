---
title: "crontab and daylight savings?"
date: 2010-11-12
forum: General Help
---

### Post by BatteryKing on 2010-11-12
I recently set up some new cron jobs under Ubuntu 10.04 64-bit (all the latest patches as of Nov. 11th) and just happened to check right after one was supposed to run and it hadn't run yet.  Checking the logs I found the previous cron job ran exactly one hour later than it was supposed to.

Is there something going on with Ubuntu 10.04, cron, and daylight savings where cron pretends daylight savings never happened or something?

---

### Post by lmarmisa on 2010-11-12
The command **man cron** explains the expected behavior of cron in relation with the daylight savings:
[INDENT][I]...
cron then wakes up every minute, examining all stored crontabs, checking each command to see if it should be run in the current minute.  When executing commands, any  output  is  mailed  to  the owner of the  crontab  (or to the user named in the MAILTO environment variable in the crontab, if such exists).  The children copies of cron running these processes have their name coerced to uppercase, as will be seen in the syslog and ps output.[/I]

*Additionally, cron checks each minute to see if its spool directory's modtime (or the modtime on /etc/crontab) has changed, and if it has, cron will then examine the modtime on all crontabs  and reload  those  which  have changed.  Thus cron need not be restarted whenever a crontab file is modified.  Note that the crontab(1) command updates the modtime of the spool directory whenever it changes a crontab.*

***Special considerations exist when the clock is changed by less than 3 hours, for example at the beginning and end of daylight savings time. If the time has moved forwards, those jobs which would have  run  in the time that was skipped will be run soon after the change.  Conversely, if the time has moved backwards by less than 3 hours, those jobs that fall into the repeated time will not be re-run.***
...
[/INDENT]

---

### Post by BatteryKing on 2010-11-13
But this makes it sound like cron should adjust to daylight savings.  What I am seeing is a lack of adjustment.  Sounds like something is broken.

---


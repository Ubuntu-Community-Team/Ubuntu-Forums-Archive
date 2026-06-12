---
title: "Adjust clock of remote machine using cron, problem with daylight saving time"
date: 2011-11-24
forum: General Help
---

### Post by signpainter on 2011-11-24
Hi folks,

I have to adjust the clock of a device which is connected to my pc via RS232. I therefore added an entry to crontab which calls a script hourly which sends the command to set the clock on the remote device to the current time of my pc. This just works great in 98.86% of the cases.

The only time it fails is in fall when daylight saving time ends. The job is executed at 1am, 2am and at 3am, but between the calls at 2am and 3am are now 2 hours and cron won't execute the job at 2am twice, when time is set back to 2am from 3am. Therefore the time on the remote device laggs for one hour an hour. Which isn't that nice.

The problem could be solved if cron would call the job a second time after the clock has been reset to 2am. Is this possible? If not, any other ideas?

Thanks alot!

signpainter

---

### Post by hwttdz on 2011-11-24
Don't think of it as the time changing, think of it as the time zone changing.  I'm guessing your computer doesn't actually see 2 exactly twice (otherwise I'd guess it would run the job twice).  So maybe set it to run every hour plus one minute, you still get updates at the same frequency, and one minute should give your machine enough time to figure out if it's daylight savings.

# m h dom month dow
1 * * * * updatetime

instead of 

0 * * * * updatetime

---

### Post by signpainter on 2011-11-25
This was actually my first idea and I didn't start to make any thoughs about DST until I read this is in the man pages of cron:

> Special  considerations  exist when the clock is changed by less than 3
       hours, for example at the beginning and end of daylight  savings  time.
       If  the time has moved forwards, those jobs which would have run in the
       time that was skipped will be run soon after the  change.   Conversely,
       if  the  time has moved backwards by less than 3 hours, those jobs that
       fall into the repeated time will not be re-run.This says to me, that a cronjob like '1 * * * * updatetime' would run on 1:01am, 2:01am and then on 3:01am. The second time the job should be executed on 2:01am after time zone has changed will not be re-run. Or am I wrong here?

---


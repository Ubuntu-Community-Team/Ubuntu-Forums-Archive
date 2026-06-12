---
title: "what does cron do with tasks scheduled while the computer is off?"
date: 2011-04-29
forum: General Help
---

### Post by fuzzylogic25 on 2011-04-29
Basically what i wanted to know is, if we turn the computer off (or hibernate/standby) - what will cron do with the tasks that were suppose to be scheduled during that time period the moment u turn it back on?

Reason i ask is because i have a backup scheduled for every single hour. and another one i want to schedule for every 15mins. If i turn my comp in standby overnite, i certainly dont want to turn it on in the morning to find cron doing like 30 back up jobs!

---

### Post by DaithiF on 2011-04-29
> **fuzzylogic25 said:**
> Basically what i wanted to know is, if we turn the computer off (or hibernate/standby) - what will cron do with the tasks that were suppose to be scheduled during that time period the moment u turn it back on?

Nothing, ie those jobs are ignored, cron does not try to 'catch-up'

This will be the behaviour for any jobs defined in your crontab (ie. crontab -e) or the system crontabs (both /etc/crontab and the root user's crontab, ie. the one edited via sudo crontab -e).

Just to note that for certain cron directories ... e.g. /etc/cron.daily, cron (on ubuntu) delegates the running of the jobs to anacron rather than running them itself.  The behaviour of anacron is different, it will try to allow for time when the computer is turned off and run the jobs as best it can to approximate the frequency you asked for.

---

### Post by sj1410 on 2011-04-29
crond needs to be running to execute the cron jobs. Theres anacron, Unlike cron, it does not assume that the machine is running continuously. For each job, Anacron checks whether this job has been executed in  the last  n  days,  where  n is the period specified for that job.  If not, Anacron runs the job's shell command, after waiting for the  number  of  minutes specified as the delay parameter.


more in 
```

man anacron

```

---


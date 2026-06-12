---
title: "cron-fusion"
date: 2010-11-28
forum: General Help
---

### Post by conradin on 2010-11-28
Hi all,
I'm trying to use cron to schedule a script I wrote.
in the terminal I'm typing sudo cron
but i get this message back.
cron: can't lock /var/run/crond.pid, otherpid may be 3332: Resource temporarily unavailable

what's going on here? how can I schedule my script to run?

---

### Post by DaithiF on 2010-11-28
> **conradin said:**
> 
in the terminal I'm typing sudo cron


cron is the daemon process that runs scheduled jobs.  its already running.  thats what the error message is trying to tell you.  you don't want to run the daemon, you want to add a scheduled job.

have a look here:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

there are several methods, the crontab command, the /etc/crontab file, the etc/cron.{hourly|daily|weekly|monthly} directories, /etc/cron.d ...

---

### Post by conradin on 2010-11-30
Hi,
I figured it out, I just forgot how to edit cron, using crontab -e

---


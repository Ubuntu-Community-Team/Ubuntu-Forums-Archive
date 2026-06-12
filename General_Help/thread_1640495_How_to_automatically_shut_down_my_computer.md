---
title: "How to automatically shut down my computer"
date: 2010-12-07
forum: General Help
---

### Post by frogknowledge on 2010-12-07
Every night I would like my computer to shut down say around 1am. I have  Gnome Scheduler, but can't tweak it to work.

I don't care about programs running just shut down everything at the same time every night would be great.

Ubuntu 10.10 Maverick
Thanks allot.

---

### Post by matt_symes on 2010-12-07
Hi

I would use cron to schedule the shutdown.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

with an entry something along the lines of

* 1 * * * /sbin/shutdown now

and added to roots crontab.

Kind regards

---


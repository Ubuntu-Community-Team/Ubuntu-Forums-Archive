---
title: "crontab disappeared"
date: 2011-04-27
forum: General Help
---

### Post by sr_guy on 2011-04-27
Ubuntu 10.10 64bit

Some of my daily tasks in my root crontab didn't take place today. When I went into crontab (crontab -e) it reverted back to it's default state. Has anyone seen this happen before?

---

### Post by fabioleitao on 2011-04-30
Just happened to me... a couple of days ago I know they were there cause I had to comment an entry in the root's crontab for some tests I was doing.

When I was done (today), I've tried to uncomment them (sudo crontab -l) and it was gone (empty?  :-/ ). sudo crontab -e tells me there file is empty, and there is no root file in the /var/spool/cron/crontabs also.  :-O

I think I am goning to cry now a bit, and then post a bug report.

---


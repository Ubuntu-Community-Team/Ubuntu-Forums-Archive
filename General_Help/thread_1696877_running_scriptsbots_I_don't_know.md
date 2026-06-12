---
title: "running scripts/bots? I don't know?"
date: 2011-02-28
forum: General Help
---

### Post by Hi-Ho-Silver! on 2011-02-28
Hi, 

I figured this is where this belongs. 
Anyway, today I got interested in the terminal after learning a few things and I got to wondering, is there anyway possible to make my very own script? As in say, to do things on its own or in other words "auto." while I am afk. Does anyone have any insight at all onto how I would get started on something like this? 

Thanks:D

---

### Post by mikewhatever on 2011-02-28
Yes, look into crontab.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by seawolf167 on 2011-02-28
> **mikewhatever said:**
> Yes, look into crontab.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Aye, read up on [writing bash scripts]("http://mywiki.wooledge.org/BashGuide"), then once you get your bash script perfected (or even a one line command), place an entry in /etc/crontab and have it run at periodic intervals

---


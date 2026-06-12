---
title: "Very large log files"
date: 2010-06-16
forum: General Help
---

### Post by Oak37 on 2010-06-16
Hi,

I recently started receiving warning messages that my root partition was running out of disk space. I have an 80Gb HDD with / and /home on separate partitions (for easier upgrading). My / partition is ~10Gb in size which I thought would be ample enough. After getting the error message it appears that my /var/log folder is taking up 5Gb of space with the biggest culprits being: kern.log; kern.log.1; messages; messages.1; syslog; ufw.log; and ufw.log.1.

I've since disabled ufw to temporarily stop writing its logfile and give me some relief. Am I right in thinking I can safely delete the logfiles with a suffix of 1? e.g. kern.log.1 as these are just older logfiles that haven't been compressed?

Is there any way to automatically keep an eye on large logfiles and delete them in the future?

Thanks for your help.

---

### Post by TeoBigusGeekus on 2010-06-16
Install bleachbit, the CCleaner equivalent in linux.

---

### Post by Oak37 on 2010-06-16
Thanks for that TeoBigusGeekus, it's already helped and looks quite useful for the future :)

---

### Post by john newbuntu on 2010-06-16
Take a look at those logs and see what it is trying to tell.  Perhaps it is something critical or just  some informational stuff.  My ufw logs are only a couple of KB.

Maybe there is information that keeps repeating several times.  Post a few of those lines and someone in this planet can help you out.

Make sure that logs are getting rotated often.  In other words, you should generally not have more than 2 or 3 logs that start with ufw or messages.  Otherwise, you might have to fine tune logrotate.

---

### Post by Oak37 on 2010-06-18
> **john newbuntu said:**
> Take a look at those logs and see what it is trying to tell.  Perhaps it is something critical or just  some informational stuff.  My ufw logs are only a couple of KB.

Maybe there is information that keeps repeating several times.  Post a few of those lines and someone in this planet can help you out.

Make sure that logs are getting rotated often.  In other words, you should generally not have more than 2 or 3 logs that start with ufw or messages.  Otherwise, you might have to fine tune logrotate.

I was thinking the same thing, especially considering that I had only enabled ufw a number of days before. Looking at a few of the logs there are huge amounts of messages relating to ufw in the order of 5 or 6 entries a second. Since disabling ufw the logs have calmed down.

---

### Post by zantalesblog on 2010-06-18
Umm

---

### Post by ben2talk on 2010-11-07
> **Oak37 said:**
> I was thinking the same thing, especially considering that I had only enabled ufw a number of days before. Looking at a few of the logs there are huge amounts of messages relating to ufw in the order of 5 or 6 entries a second. Since disabling ufw the logs have calmed down.

Excellent - I just got the same conclusion. This morning I hung around resizing - moving partitions and resizing root from 30GB to 40GB and moving it left. Left the thing running with some torrents for 6 hours and came home to the same warning.

I got the message, allowed a scan and traced to the log directory finding 'messages' and 'ufw' and 'kernel' were at around 2.2 to 2.7GB with several backups at the same size - that's a whopping 7GB for the current and 8.1GB for backup.1, then 8.1GB for backup.2 etc. Crazy - deleted them to get back the space and turned logging down in UFW to 'low'.

UFW is the only change I'm aware of for logging in the last month or so.

---


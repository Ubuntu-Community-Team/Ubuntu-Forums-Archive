---
title: "Freezes and cron.hourly"
date: 2010-02-09
forum: General Help
---

### Post by pigreco on 2010-02-09
I have  had a weird problem over the last days. It happens sometimes that my Ubuntu 9.04 64 bit based system freezes. What sounds strange is that it freezes only in a specific minute. That means, if it freezes it happens at minute 17 and not every hour. At minute 17 of any hour run-parts script execute scripts in cron.hourly. By the way, I have no script in cron.hourly.

Do you have any clue?

---

### Post by rnerwein on 2010-02-09
hi
have you looked in /etc/anacrontab ? 
see man anacron. anacron will notic the work to do with a time stamp. but when the system realy freezes there is may be no time stamp. 
in my anacrontab is nothing to start at minute 17.
may this helps.
ciao

---

### Post by pigreco on 2010-02-09
Thanks for the reply.
I read the crontab file. I think the part of my interest is:

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly

As you can see, this process is executed at minute 17.

---

### Post by pigreco on 2010-02-10
I commented the line related to cron.hourly in crontab, namely cron.hourly doesn't execute. I admit that it's not a good thing in general. By the way, over the last 24 hours I've not experienced any freeze. I will keep updated this thread during the next days.

---

### Post by SNo0py on 2011-09-22
Hm, same problem with the latest Ubuntu version, nothing in /etc/cron.hourly and freezes.

From /var/log/syslog:

```

Sep 22 10:17:01 mike CRON[14132]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 22 11:18:59 mike kernel: imklog 4.6.4, log source = /proc/kmsg started.

```

Any ideas what is causing this?

---


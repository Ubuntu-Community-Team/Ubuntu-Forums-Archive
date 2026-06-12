---
title: "How to make a file execute at intervals of time / scheduling"
date: 2012-08-02
forum: General Help
---

### Post by nsubage on 2012-08-02
Hi to all,
I have developed a system that read sms from gsm modem through gammu and sores in kalkun database. I have a php file that can read the inbox and reply back the sms. I want it to be executed at several interval of time after logging in. How could i do it?
Thanks in advance.

---

### Post by iperich on 2012-08-02
I don't understand you question well: do you want to execute the script 1 time after a certain amount of time or you want to execute the script "infinite" times separated by an amount of time?

For the 1st case, you could use a shell script and put in on startup, something like:

#!/bin/sh
sleep 60
php file.php

for a 60 seconds pause after startup. You should have installed the php5-cli package for this. 

For the second case, you can use cron, is very simple and you can execute the php script up to 1 time per minute. there's a lot of information in the web about how to configure the crontab file, and you can configure it executing "crontab -e" in the console.

---

### Post by audiomick on 2012-08-02
I think you need a thing called crontab. I have no idea how it works,  but I have read often enough that it is the thing to use for scheduled tasks. Here is a page on it from the Ubuntu documentation.

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by Ralph L on 2012-08-02
gnome-schedule is a gui for cron.  It is installable with synaptic.  If you want a more complete scheduler you might look at fcron/fcronq.  It has a lot more options, and I got it working in Lucid.  However, I did have some trouble with compiling and installation, and conflicting with cron.

---

### Post by Lars Noodén on 2012-08-03
[at](http://manpages.ubuntu.com/manpages/precise/en/man1/at.1.html) is another option.  Neither at nor cron are that accurate and can be off by a few seconds or more.

---

### Post by Grenage on 2012-08-03
Aye, if you don't need atomic accuracy, you can use crontab.  I've never had an instance where cron wasn't accurate enough, but I'm one man.

```
*/5 * * * * /usr/bin/xxx
```

Would run every 5 minutes, as an example.

---


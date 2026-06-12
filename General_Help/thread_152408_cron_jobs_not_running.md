---
title: "cron jobs not running"
date: 2006-03-29
forum: General Help
---

### Post by chusome on 2006-03-29
I've followed the instructions at: [https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto) and I've even used Kcron to create a job and the successfully ran it manually through kcron, but the jobs don't run as scheduled.
When I open the system-monitor it has cron listed as a running service (cron not crond, if that matters)

Currently a crontab -l puts out:
# test
5 20 * * *      /home/matt/Desktop/tbird.sh
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

tbird.sh is a script I run to start thunderbird for purposes of testing this, and it does work. Is there something that needs to be activated? (cron is checked off in my list of services)

---

### Post by professor_chaos on 2006-03-29
I see your trying to run the script at hour 20 and minute 5, or 20:05.

Try and run the script via "/home/matt/Desktop/tbird.sh". 
does it work?

---

### Post by chusome on 2006-03-29
Yes, the script works

---

### Post by dcstar on 2006-03-30
[QUOTE=chusome]I've followed the instructions at: [https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto) and I've even used Kcron to create a job and the successfully ran it manually through kcron, but the jobs don't run as scheduled.
When I open the system-monitor it has cron listed as a running service (cron not crond, if that matters)

Currently a crontab -l puts out:
# test
5 20 * * *      /home/matt/Desktop/tbird.sh
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

tbird.sh is a script I run to start thunderbird for purposes of testing this, and it does work. Is there something that needs to be activated? (cron is checked off in my list of services)[/QUOTE]
Running a script in a **terminal environment** does not mean that the script will run under cron.

You have to set up any various environment "assumptions" that are available in your terminal session that your script needs, for example does your script have something like this in the first line:
```
#!/bin/sh
```

---

### Post by chusome on 2006-03-30
Here's the script contents:
#!/bin/bash
mozilla-thunderbird

As I stated earlier when I run the task manually through Kron it runs perfectly. As well this goes far beyond the script. Even the examples here: [COLOR="Blue"]https://wiki.ubuntu.com/CronHowto[/COLOR] do not run.

---

### Post by chusome on 2006-03-30
Also I don't care about the script, all I want to see is a working cronjob.
If anyone wants to post a sample test job, I'll try it.

---

### Post by ubuntumaneh on 2006-03-30
Have you tried this:
5 20 * * * /usr/bin/mozilla-thunderbird

Either use the complete path for mozilla-thunderbird in the script or just plug the above in the crontab. the script could be:
#!/bin/bash
/usr/bin/mozilla-thunderbird

EDIT: a more elegant way would be to set properly the variable PATH. So in crontab write:
PATH = /usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin:

Then we would be able to drop the paths in the script.

---

### Post by chusome on 2006-03-30
tried 
17 17 * * * /usr/bin/mozilla-thunderbird

a few minutes ago and still no go, its like the daemon isn't actually running.

---

### Post by ubuntumaneh on 2006-03-30
[QUOTE=chusome]
a few minutes ago and still no go, its like the daemon isn't actually running.[/QUOTE]

This is not so precise, but try to restart the daemon then:
cd /etc/init.d
sudo ./cron restart

---

### Post by chusome on 2006-03-30
Ran those commands and got:
* Restarting periodic command scheduler...                              [ ok ]

So it appears to be running ok, so then I did:
crontab -e
and added
18 18 * * * /usr/bin/mozilla-thunderbird
then confirmed with
crontab -l

I set the job at precisely 18:16 and waited for 18:18 come. When the clock struck, still nothing happens. Afterwards I ran the job manually from kcron and it did run.

I'm starting to think this just wasn't meant to be.......

---

### Post by ubuntumaneh on 2006-03-30
Try something else, just to see what is going on. try something like xterm:

40 * * * * /usr/bin/xterm

One other thing you may try just to test:

41 * * * * echo "hope it works" >> cron_test

and then see if it appear the file cron_test.

---

### Post by ubuntumaneh on 2006-03-30
Ok. I think I know the problem. In the beginning of the crontab file put the following:

DISPLAY=:0.0
#tes
40 * * * * /usr/bin/mozilla-thunderbird

I tried here with firefox, with the variable DISPLAY unset it did't open, but with the variable set, it opene. So I believe it will work for you.

---

### Post by chusome on 2006-03-31
Thank you ubuntumaneh
We have lift off!!!

---


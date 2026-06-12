---
title: "Cron Job for Updates"
date: 2011-11-27
forum: General Help
---

### Post by jim_deadlock on 2011-11-27
I'm trying to get this working as a root cron job:

```
@reboot /usr/bin/apt-get update && /usr/bin/apt-get -y upgrade
```

... but it's not running the job and I get the following in syslog:

```
Nov 27 10:28:01 alec cron[1035]: (root) RELOAD (crontabs/root)
Nov 27 10:28:01 alec CRON[3196]: (root) CMD (/usr/bin/apt-get update && /usr/bin/apt-get -y upgrade)
Nov 27 10:28:07 alec CRON[3195]: (CRON) error (grandchild #3196 failed with exit status 100)
Nov 27 10:28:07 alec CRON[3195]: (root) MAIL (mailed 1 byte of output; but got status 0x00ff, #012)
```

It seems to be the upgrade part causing the error because running it individually like this also produces the error:

```
@reboot /usr/bin/apt-get -y upgrade
```

Running this command directly from the terminal works fine but I can't seem to get it to play ball as a cron job :confused:

---

### Post by gmargo on 2011-11-27
Trying to do anything significant "@reboot" is probably not the best idea.  Perhaps use a regular scheduled entry?  Alternatively you can install the package designed for this: **unattended-upgrades**.

---

### Post by gdonwallace on 2011-11-27
Is this in the root-cron or the user-cron.

You have to run these commands with root privileges.  

Also, in the root cron, add it as a regular cron job, calling a script file to do the upgrade.

---

### Post by mswoon on 2012-01-06
Try adding: 

SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

to the crontab. That works for me every time cron fails; I don't know exactly what causes it - on a fresh clean install, cron works *without* those lines, but over time, after a few updates at night, eventually, cron will fail, and I have to add those two variables so that my updates work.

---

### Post by von Stalhein on 2012-10-05
> **mswoon said:**
> Try adding: 

SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

to the crontab. That works for me every time cron fails; I don't know exactly what causes it - on a fresh clean install, cron works *without* those lines, but over time, after a few updates at night, eventually, cron will fail, and I have to add those two variables so that my updates work.

Sorry for the thread resurrection!!

I've been havingthe same trouble since 11.04. Cron used to run fine, but now I can't get it to go, and have that error ```
mailed 1 byte of output; but got status 0x00ff, #012
```

Just for a n00b, where in the crontab would your suggestion above go?

The simple cronjob I'm trying to run is ```
59 01 * * * deluge-gtk
01 08 * * * killall deluge-gtk
```

Thanks!

---


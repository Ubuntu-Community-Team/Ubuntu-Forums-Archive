---
title: "Do I need these services?"
date: 2010-01-07
forum: General Help
---

### Post by oxf on 2010-01-07
I'm Using 9.04/Gnome.  I was looking in System>Administration>Services and wonder if I need them All of below enabled? It seems like duplication to me.  

anacron
aTD
cron

Thanks

---

### Post by falcon1620 on 2010-01-07
There may be services using all 3 cron's to run administrative tasks, if you are curious you could check out all of the cron configurations and see if there are any scripts in each one to look at. 

> 
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly



And atd and Cron both seem to have similar results... It would appear that they have tried to fix some of the cron problems with a system not always on, so anacron is used to remedy this and atd is a que style cron system for later execution. Most of the configs are in /etc/ and /etc/anacron /etc/crond.d and the rest of the /ect/cron.files where scripts are located. oh don't forget about the /etc/crontab file that points directly to anacron. you can type into a terminal man anacron or man atd if you would like to learn more about these programs and how they interoperate. The overall answer is yes you should leave them enabled, so I would say no they are not all redundant with this particular configuration. ;)

---

### Post by Enigmapond on 2010-01-07
This thread might be helpful. It was created for a request to speed up the boot but it lists the services that you need running and those you don't really need...

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It's helped me to shut some services down that I wasn't using and actually I boot up much faster as well..

Cheers!

---

### Post by oxf on 2010-01-13
> **Enigmapond said:**
> This thread might be helpful. It was created for a request to speed up the boot but it lists the services that you need running and those you don't really need...

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It's helped me to shut some services down that I wasn't using and actually I boot up much faster as well..

Cheers!

Many thanks..very useful!

---


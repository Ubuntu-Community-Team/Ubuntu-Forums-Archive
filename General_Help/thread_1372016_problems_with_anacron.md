---
title: "problems with anacron"
date: 2010-01-04
forum: General Help
---

### Post by ittayd on 2010-01-04
I work with my laptop at work and home. 

It seems that anacron runs every time the laptop plugs into AC power, which is understandable, given that I wouldn't like to waste precious battery power on the jobs it executes. 

However, what I'm experiencing is this: in the morning I unplug the laptop, drive to work and plug it back in. So anacron is executed and starts running the daily jobs, which means I cannot work with my laptop (incidently, if someone can recommend a way in which updatedb.mlocate and prelink.bin can run without causing all desktop applications to suffer, I'll be very interested)

When coming back home, I plug the laptop to AC power. What I would like is for anacron to run somewhere around 3AM. 

How is this possible?

Thank you,
Ittay

---

### Post by gsmanners on 2010-01-04
I think anacron is triggered by cron, and the configuration for that is in /etc/cron.d/anacron:

```
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
30 7    * * *   root	start -q anacron || :
```

The above starts anacron at 7:30. See [https://help.ubuntu.com/community/CronHowto#Crontab%20Sections](https://help.ubuntu.com/community/CronHowto#Crontab%20Sections)

I think you may be able to edit this to control when cron attempts to launch anacron.

---


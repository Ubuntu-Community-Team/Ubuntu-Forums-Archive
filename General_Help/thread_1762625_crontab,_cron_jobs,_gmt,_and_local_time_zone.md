---
title: "crontab, cron jobs, gmt, and local time zone"
date: 2011-05-19
forum: General Help
---

### Post by robertbub on 2011-05-19
It seems that my cron jobs are never executed in my current timezone.

I checked the hardware clock (UTC-based) via hwclock and it is correct.  The system date/time is also correct.  /etc/default/rcS contains "UTC=yes".

Even restarting cron after boot does not fix the problem.

The cron jobs always try to execute as if the times were specified in GMT, not in my local time zone.

How might I diagnose this problem?

Thanks.

---

### Post by seawolf167 on 2011-05-19
Please run

```
dpkg-reconfigure tzdata
```

to reconfigure your timezone, then restart the cron service

```
sudo service cron restart
```

and see if that fixes your problem

---

### Post by duke.tim on 2011-05-19
(these links may help) Double check that you setup your cron jobs correctly :)

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)
[http://manpages.ubuntu.com/manpages/maverick/man5/crontab.5.html](http://manpages.ubuntu.com/manpages/maverick/man5/crontab.5.html)

I hope this helps

---

### Post by robertbub on 2011-05-19
> **seawolf167 said:**
> Please run

```
dpkg-reconfigure tzdata
```

to reconfigure your timezone, then restart the cron service

```
sudo service cron restart
```

and see if that fixes your problemThis fixed it.

Apparently, **/etc/timezone** had just ```
US
``` in it (i.e., an invalid timezone).  I discovered this by looking at **/proc/PROCESS-ID-OF-CROND/environ** and saw that the *TZ* environment variable was wrong.

Thanks!

---

### Post by seawolf167 on 2011-05-21
Awesome, I love easy fixes :)

---


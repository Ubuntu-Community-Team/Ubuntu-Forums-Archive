---
title: "how to write alarm script exact time"
date: 2010-12-20
forum: General Help
---

### Post by psihokiller4 on 2010-12-20
ok I followed this page:

[http://ca.ubuntuforums.org/showthread.php?p=1343270](http://ca.ubuntuforums.org/showthread.php?p=1343270)

that script seems good but I want to change

I want if program is running that it wakes up program on each day (example at 17:15)

so I don't want to put it in to sleep but in to time waiting

---

### Post by psihokiller4 on 2010-12-20
*BumP*

---

### Post by psihokiller4 on 2010-12-20
bump

---

### Post by psihokiller4 on 2010-12-20
bump

---

### Post by efflandt on 2010-12-20
That is what cron is for which can run something regularly at any set day of week or month, or time of day, or interval. In a terminal see:

```
man cron
man crontab
man 5 crontab
```If you want something to run as root use **sudo crontab -e** to configure it.  If you want it to run as you do **crontab -e**.  Note that the environment will be minimal, so it is best to assume no environment, export any environment you need and/or use full paths (not shortcuts like ~/ or $HOME/ ).

Although, if you just want to set an alarm to do something once only, you might web search "linux rtc".

---

### Post by psihokiller4 on 2010-12-20
thank you very much

problem solved

---


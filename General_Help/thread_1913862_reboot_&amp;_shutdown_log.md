---
title: "reboot &amp; shutdown log"
date: 2012-01-23
forum: General Help
---

### Post by sj1410 on 2012-01-23
Hi, 

i have created a script "S02BOOTLOG" in /etc/rc6.d/ with

```

logger -p local7.err -t BOOT "system rebooted"
```


so that i get a log when the system is rebooted, but its not working.

---

### Post by Metabaron on 2012-02-27
The syslog daemon probably doesn't run. Try cat the process list to a file before you run logger to check.

---


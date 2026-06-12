---
title: "Huge /var/log files"
date: 2011-07-07
forum: General Help
---

### Post by acrane1 on 2011-07-07
So I noticed today that my machines root hard drive had almost no space on it. I did a disk usage analyzer and I found out my var/log folder is 95GB. The large logs are:
-rw-r-----  1 syslog   adm   47G 2011-07-07 19:09 kern.log
-rw-r-----  1 syslog   adm   20G 2011-07-07 19:23 syslog
-rw-r-----  1 syslog   adm   28G 2011-07-07 07:35 syslog.1
-rw-r--r--  1 root     root  1.6M 2011-05-27 01:27 dpkg.log.1

can I just delete them? also how can I stop this from happening again?

---

### Post by ubername on 2011-07-07
Something is writing tons of info into the logs. That is not standard behaviour, but to identify what is wrong you will need to look at the logs to see what the problem is. Try

```
tail -n20 /var/log/syslog
```
and
```
tail -n20 /var/log/kern.log
```
to see if that shows anything odd (like a lot of repeating messages).
I think you can safely get rid of any logs ending in .1 (and higher)

---


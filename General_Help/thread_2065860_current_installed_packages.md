---
title: "current installed packages"
date: 2012-10-03
forum: General Help
---

### Post by micahpage on 2012-10-03
I know
```
dpkg --get-selections

```
will show "all" my packages installed

I was looking for all packages "I" installed, not dependencies of upgrades or updates or default ubuntu packages, etc. Like packages i have manually installed via ```
sudo apt-get install <package>
```

Is there a way to figure this out?

---

### Post by jerrrys on 2012-10-03
maybe

/user/share/applications

---

### Post by oldos2er on 2012-10-03
Look in /var/log/apt/history.log

---

### Post by micahpage on 2012-10-04
> Look in /var/log/apt/history.log

that is exactly what i was looking for, except the log only goes back the last 4 days. I was hoping to get all

so far /usr/share/applications seems to be the only possibility?

---

### Post by drmrgd on 2012-10-04
Check that same folder for a previous history logfile that is compressed as an archive (like history.log.1.gz).  That will pick up prior to 4 days ago, and depending on how you log system is setup and how long you've been running your system, you may have even older, archived logs.

---


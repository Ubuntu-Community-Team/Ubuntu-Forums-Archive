---
title: "Installed app history?"
date: 2010-08-14
forum: General Help
---

### Post by Ultra_Man on 2010-08-14
Is there some sort of app or log file that has a history of when I installed an application or is Ubuntu Software Center the first to have it? I use aptitude most of the time by the way.

---

### Post by Rubi1200 on 2010-08-15
System > Administration > Log File Viewer > dpkg.log

Alternatively, from the terminal:
```
gedit /var/log/dpkg.log
```

Or, in Synaptic Package Manager:
File > History

---


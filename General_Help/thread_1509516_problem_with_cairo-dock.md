---
title: "problem with cairo-dock"
date: 2010-06-14
forum: General Help
---

### Post by abhot on 2010-06-14
i am using cairo-dock version 2.1.3..
the problem is at system start up the configuration window of cairo-dock automatically opens
when i close the window the dock appears but the there is no switcher
if i restart the machine without switcher applet enabled it works fine..

---

### Post by fabounet on 2010-06-15
try to launch the dock with a delay on startup, using the command :
```
sleep 10 && cairo-dock
```
try with 15 is 10s is not enough

---


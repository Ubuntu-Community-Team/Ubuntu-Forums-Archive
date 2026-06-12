---
title: "Bluetooth misbehaves after installing KDE"
date: 2011-04-27
forum: General Help
---

### Post by Jezdec on 2011-04-27
I've had a number of problems with bluetooth running under Gnome ubuntu 10.10 on a Dell Inspiron N7010 with Dell Wireless 365 Bluetooth   Module. I mainly use bluetooth to browse files on my phone. I would frequently get file transfers to the phone hang. And, the bluetooth icon would disappear from the taskbar after after a resume from sleep. At first, I thought the fix from [here would help, but it didn't entirely fix the problem.]("http://ubuntuforums.org/showthread.php?t=1387211")

Later, I realized that the problem showed up after I had installed KDE. Then I found that uninstalling bluedevil, the bluetooth stack for KDE, made everything better. So now I have working bluetooth again.

---

### Post by Jezdec on 2011-04-28
Looks like I spoke too soon. Removing bluedevil improved things considerably, but after about 10 cycles of sleep / wake, the bluetooth icon disappeared, and sleep as well as bluetooth stopped working. This is a symptom it had before, it just never survived 10 cycles, just one or so.

---


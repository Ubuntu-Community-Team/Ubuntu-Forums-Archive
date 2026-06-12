---
title: "Home partition appears to be full... but is should not"
date: 2010-03-14
forum: General Help
---

### Post by mystrangeusername on 2010-03-14
Hi, I mount /home on its own partition that it is 20GB wide.

I used 8GB in /home/b. /home contains just /home/federico & /home/lost+found (which appears to be empty).

Strangely the partition appears to be full. I kept deleting files (and deleting also the Trash) but after I while my partition was full again.

I do not use a swap file on this partition.

I really do not understand why the partition appears to be full...

---

### Post by Barriehie on 2010-03-14
See if perhaps ~/.xsession-errors is the culprit.

---

### Post by pastalavista on 2010-03-14
Open Nautilus as root```
gksudo nautilus
```Show hidden files. You should see more. You can use Disk Usage Analyzer in the System | Administration menu. If it isn't there (I don't remember if I installed it but don't think I did)```
sudo apt-get install baobab
```

---


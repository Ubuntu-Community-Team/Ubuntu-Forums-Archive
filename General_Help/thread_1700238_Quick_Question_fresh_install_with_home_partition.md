---
title: "Quick Question fresh install with /home partition"
date: 2011-03-04
forum: General Help
---

### Post by bananafeller on 2011-03-04
Ok i would like to confirm this before i go ahaed and do it. i have my /home saved on a separate partitions. i want reinstall the os and set my current /home as my /home. so do I just select install / on the first partition and set the mount point of my (/home) partition as /home with the <foramt partition> option not selected?

SO i guess my question is if i already have /home on a seperate partition how do i fresh install.

---

### Post by 3Miro on 2011-03-04
1. BACKUP EVERYTHING IMPORTANT SO THAT IF THINGS GO WRONG YOU WILL NOT LOSE ANYTHING.

2. Say you have three partitions, sda1, sda2 and sda3. sda1 is currently swap, sda2 is / and sda3 is /home make sure you know which partition is which either by size or file system or physical location on the drive (beginning, end, middle)

3. During install, go for "advanced/custom" option for partitions

4. Select sda1 to be swap (you don't have to format), sda2 to be / (format it) and sda3 to be /home (DO NOT FORMAT)

The only problem that you may run into is with the settings folders .something. On a fresh install it is a goo idea to delete .gnome2, .gconf, .gconfd and .config (keep .mozilla and .config/chromium if you want your old browser settings)

---

### Post by bananafeller on 2011-03-04
thanks a lot. thats what i thought but i didn't want to take the risk.

---


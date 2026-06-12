---
title: "Ubuntu 9.10 no partition table"
date: 2009-10-31
forum: General Help
---

### Post by atomhearth on 2009-10-31
**When I get the partition table moment while I am installing, there' s no partitions. Ubuntu show me all the 500GB, but I have 300GB, 100GB, 60GB and 40GB. Why I can not see all partitions but just one big? I don' t want to formate all this sh*t. I have my music, movies, documents....Help pls and sorry for thr broken english !******

---

### Post by don-juan on 2009-11-02
This is a known issue. I don't know exactly if this problem occurs in all the installation media, but i recognised, that with the alternate installation medium, you can choose if you want to activate the serial ata raid drivers (or something like this). This means, you can activate dmraid for fakeraid sata/ata controllers. You have to deactivate this option, if you do not want to use the fakeraid. If you use the desktop installation medium you just have to boot the medium with the kernel option "nodmraid" in order to deactivate it for the whole installation time. If you do not want to use dmraid after installing the system, you may have to purge the dmraid package, because it will allways be installed during the installation process, and you can't deactivate it. Therefore you have to chroot into your new installed system direct after your installation without rebooting first. Then you execute "aptitude purge dmraid" and everything goes fine with your new system.

cheers
don-juan

PS: It is possible, that this solves your problem. Maybe your problem is about something else...

---


---
title: "External HD device keeps changing"
date: 2009-12-06
forum: General Help
---

### Post by miscreant on 2009-12-06
So, I have an external hard drive setup as a backup drive on my box, and I want to automount it in fstab, but it keeps changing which device it is in /dev. Sometimes it'll be /dev/sdb, sometimes /dev/sdf. Almost seems like it depends on whether boot detects the HD or the media card reader first, but it seems to be random. Kinda at a loss as to what to do, unless I try and mount ALL the different devices at startup.

---

### Post by bingoUV on 2009-12-06
You need to stop depending on sdb, sdf etc. Linux does not guarantee persistence of device name between reboots. Use UUID to point to hard disks and partitions. How? Read

[http://ubuntuforums.org/showthread.php?t=1340530](http://ubuntuforums.org/showthread.php?t=1340530)
[http://ubuntuforums.org/showthread.php?t=1342524](http://ubuntuforums.org/showthread.php?t=1342524)

---


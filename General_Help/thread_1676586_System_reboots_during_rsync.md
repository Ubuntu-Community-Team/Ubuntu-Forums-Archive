---
title: "System reboots during rsync"
date: 2011-01-27
forum: General Help
---

### Post by tweakz on 2011-01-27
I am running running ubuntu server 10.10 64bit. The system is brand new hardware with a
intel i7 950 and 24gb of non-ecc ram. The system is rebooting when I am trying to do a rsync to my softraid array. When I start the rsync it runs for about 45 seconds then the reboots. I ubuntu installed on a softraid raid0 array on /dev/md0 my swap device is running under /dev/md1 and the raid I am copying to is located under /dev/md2. I have looked under /var/log/debug /var/log/messages /var/log/dmesg /var/log/kern.log /var/log/daemon.log. After the reboot my /dev/md2 raid array starts a resync. It has done this to me 3 times in a row and I have to wait 8+ hours for the resync to finish before testing. Any help would be greatly appreciated, thanks!

---

### Post by tweakz on 2011-01-27
bump

---


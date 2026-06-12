---
title: "RAID 1 Array not starting at boot up"
date: 2011-01-07
forum: General Help
---

### Post by thedaynos on 2011-01-07
hi, I have two 2 TB hd's that I just put together in a RAID 1 Array last night. Took a while to initially sync but so far it seems to be working alright and nice and fast.  only problem i have with it is that every time I reboot, the state is "not running, partially assembled".  at the same time, the option in the GUI of Disk Utility doesn't let me start the array, it only lets me stop.  So I stop it, then start it, which is real easy, like 5 seconds or less, and then re-mount it and it all works again.  Only problem is after I reboot, i have to go through this process again to get it started.  any ideas?

Thanks!

---

### Post by dcstar on 2011-01-07
> **thedaynos said:**
> hi, I have two 2 TB hd's that I just put together in a RAID 1 Array last night. Took a while to initially sync but so far it seems to be working alright and nice and fast.  only problem i have with it is that every time I reboot, the state is "not running, partially assembled".  at the same time, the option in the GUI of Disk Utility doesn't let me start the array, it only lets me stop.  So I stop it, then start it, which is real easy, like 5 seconds or less, and then re-mount it and it all works again.  Only problem is after I reboot, i have to go through this process again to get it started.  any ideas?


You have to manually change the /etc/fstab and mdadm.conf (?) files. Do a web search as there already are numerous posts on this exact issue with detailed solutions.

---


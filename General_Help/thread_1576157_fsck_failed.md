---
title: "fsck failed?"
date: 2010-09-16
forum: General Help
---

### Post by garboyl on 2010-09-16
I am trying to load Ubantu 9.04 from a SD card into a Eee pc model 900A.  Each time I try the following message comes up "An automatic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed.    Help!

---

### Post by sisco311 on 2010-09-16
Hi and welcome to the forums!

After the error message you should be dropped to a BusyBox shell from where you can run e2fsck:
```
e2fsck -C0 -f -v /dev/sd**XY**
```

replace /dev/sd**XY** with the device name of the root partition (i.e. /dev/sda1).

NOTE: There is a zero (0) after the -C option, NOT an uppercase o. 

Or boot a Live CD or USB, start GParted (System -> Administration), right click  on the partition (unmount it if needed) and select **Check**.

---

### Post by garboyl on 2010-09-16
Thanks for the welcome and info.  The error message ends with:
a maintenance shell will now be started
bash: no job control in this shell

---


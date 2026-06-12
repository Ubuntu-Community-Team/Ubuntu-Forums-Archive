---
title: "After kernel upgrade Ubuntu won't boot"
date: 2010-09-01
forum: General Help
---

### Post by TheDelChop on 2010-09-01
Guys,

Title says it all, after an update of the kernel by the update manager Ubuntu no longer boots, it tells me that

"udevadm trigger is not permitted while udev is unconfigured"

then 

"Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (Did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/c2e325b9-fbd1-4402-80c0-cd088deb19e8 does not exist.  Dropping to shell!"

Then it drops me into busy box.  

Can anybody give me a tip or two as to what's going on here or am I going to need to re install ubuntu?

---

### Post by andrewkk on 2010-09-01
Same story here. And holding Shift at boot doesn't bring me to the GRUB menu so I could try using an older kernel.

```
udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/6cf18406-700e-4bc7-bc10-364ff2d017a1 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) uname -a
Linux (none) 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 unknown
(initramfs) ls /dev/sd*
ls: /dev/sd*: No such file or directory
```

Sad day.

---


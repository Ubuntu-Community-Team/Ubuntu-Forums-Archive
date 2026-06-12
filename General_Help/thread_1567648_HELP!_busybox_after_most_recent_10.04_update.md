---
title: "HELP! busybox after most recent 10.04 update"
date: 2010-09-04
forum: General Help
---

### Post by DrScum on 2010-09-04
I installed all recommended updates as suggested by the update manager, after installing was asked to restart. During this restart I get the error message "udevadmin trigger is not permitted while udev is unconfigured. After this I am left with a BusyBox v1.13.3 [...] (initramfs)_

What do I do????

---

### Post by DrScum on 2010-09-04
Found a fix myself right here:
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

In the thread I point to above they tell you to boot while holding down the shift key. In my case it was very important to "start" holding down the key at the right moment. When I held it down from the very beginning of switching on power it didn't work. Only if I hit the key after the BIOS information was being processed, the boot options window appeared, i.e. GRUB was loaded.

---


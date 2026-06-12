---
title: "After updating Ubuntu 10.4, Reboot crashed"
date: 2010-09-21
forum: General Help
---

### Post by bgdorazio on 2010-09-21
After updating Ubuntu 10.4, Reboot crashes with the following messages

     "devadm trigger is not permitted while udev is unconfigured"
     "gave up waiting for root device"

"Alert! /dev/disk/by-uuid/c70a9419/e783-4eb3-85fa-d6fc5c46adc2   Does not Exist.

 any idea on how to fix?

---

### Post by sanderd17 on 2010-09-21
How is your partition schema?

Do you have one big partition or a separate /home or windows on an other partition (or mayby wubi).

Can you boot up with a live cd and run 
```

sudo blkid

```
and show the contents of the file "/etc/fstab" in your faulty installation's root partition (so from the live cd, it should be under /media/xxx-xxx-xxx..../etc/fstab after you mounted it).

---

### Post by bcbc on 2010-09-21
That sounds like this problem [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

---

### Post by bgdorazio on 2010-09-21
That sounds like this problem [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

That thread was exactly like my problem and provided the solution
update-initramfs -u -k all

:KS :)  Thanks for the help

---


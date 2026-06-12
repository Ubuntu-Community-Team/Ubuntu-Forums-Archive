---
title: "Flash Drive Help?"
date: 2012-08-19
forum: General Help
---

### Post by Manhi40 on 2012-08-19
I just got a new flash drive, it worked fine, but then I started messing with this app called "storage device manager" and now when I try to mount the flash drive, I get this:
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)
Can I get help? also, the data on the drive is not important.
I already tried to change the options in storage device manager, and tried re-formatting it.
I then tried this: [http://askubuntu.com/questions/120233/cant-mount-ntfs-partition-without-root-access](http://askubuntu.com/questions/120233/cant-mount-ntfs-partition-without-root-access)
That didn't work either...
Please help, fast because I need to do some large file transfers...

---

### Post by llamabr on 2012-08-19
Unplug the device, plug it back in, count to ten, and post the output of:

```
dmesg | tail
```

You either need to mount it as root, or, as you mention, re-format it.  Do you really need it to be ntfs?

---

### Post by Manhi40 on 2012-08-19
[ 2579.658834] sd 6:0:0:0: [sdb] Write Protect is off
[ 2579.658845] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2579.661257] sd 6:0:0:0: [sdb] No Caching mode page present
[ 2579.661268] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2579.671199] sd 6:0:0:0: [sdb] No Caching mode page present
[ 2579.671212] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2579.707385]  sdb: sdb1
[ 2579.716679] sd 6:0:0:0: [sdb] No Caching mode page present
[ 2579.716686] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2579.716692] sd 6:0:0:0: [sdb] Attached SCSI removable disk



and ntfs seems to be the fastest fs for this drive, also re-formatting to a different fs doesn't help either... one way I made it work is by making sda1 very small and filling the rest of the space as sda2 but I don't want it that way because I still receive the error message and 2 partitions, also this only happens on my computer, for all other computer it works (the other's are also ubuntu computers)

---

### Post by Manhi40 on 2012-08-20
bump

---

### Post by Manhi40 on 2012-08-26
bump

---


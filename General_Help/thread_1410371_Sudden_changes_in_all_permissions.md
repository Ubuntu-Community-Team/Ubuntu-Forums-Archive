---
title: "Sudden changes in all permissions"
date: 2010-02-18
forum: General Help
---

### Post by kvk on 2010-02-18
I'm running 9.04, working in Emacs. Apparently, from what I can see, there is some failure of the file system or superblock partition; I'll be working along just fine when suddenly all of the data disk (separate from the OS disk) suddenly reverts to a Read-only filesystem and nothing in the root chmod will change that. Rebooting restores it for a few moments but attempted access immediately results in the lock up.

Now, I tried running fsck on the unmounted drive, but if it's unmounted, fsck can't find it. (??) If I mount it, of course, you don't want to run fsck. I also tried running

e2fsck -b 8193 /etc/media/disk

but it returned the same error message of a corrupt superblock or else an incorrect filesystem. Other attempts included

fsck -t ext3  /etc/media/disk

with similar results.

Now I can mount the disk manually using the Ubuntu GUI, but running

mount disk

from within the directory produces

"Can't find disk in /etc/fstab or /etc/mtab"

Same results when running it from the general root directory with the proper directory mapping.

Any suggestions on this one?

---

### Post by cariboo on 2010-02-19
You are trying to use the mount point of a disk that isn't mounted. use for example:

```
fsck -t ext3 /dev/sdb
```

If the drive you are trying to repair is your second hard drive. If you aren't sure of the device label type:

```
sudo fdisk -l
```

the above command will list all your hard drives as well as their partitions.

---

### Post by kvk on 2010-02-19
Thank you- that referenced the drive correctly. It ended up having so many bad sectors that I couldn't reformat it or repair the file system, so had to order a new one.

Thanks so much!

---


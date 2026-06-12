---
title: "Error mounting hard drives on startup"
date: 2011-04-16
forum: General Help
---

### Post by kaprikawn on 2011-04-16
Hi, I have 3 hard drives in my system, one with the OS on it (Lucid 64-bit) and another two media drives.  But I get an error on startup when it tries to mount my two other drives.  I do not get an error when I comment out the entries in my /etc/fstab file that mounts my two extra hard drives.

However, when I boot up, and reinstate the two entries in the /etc/fstab file and run a ```
sudo mount -a
``` it works fine.  I only get the error on startup.

My /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=05c39b13-5d4c-49a0-ab13-9852b18e2692 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdc1	/media/network1	ext3	auto	0 0
/dev/sdb1	/media/network2	ext3	auto	0 0
```

The problem is with the two mounts at the bottom.  Could anyone point me in the right direction please as to what the problem is and/or how to fix it.

There is no specific error message.  But I also had this problem before a fresh install, and I seem to remember it saying that the mount point was not available or something to that effect.

Thanks in advance.

---


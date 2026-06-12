---
title: "Error mounting external hdd after exiting virtualbox"
date: 2012-03-14
forum: General Help
---

### Post by /bee/ on 2012-03-14
I'm running 11.10 and have a Western Digital 1TB MyBook external hdd.  I got my iPhone to connect to iTunes via my XP inside virtualbox, but after I quit virtualbox I cannot access my hdd.

The error I got was:

**Unable to mount My Book**
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /media/MyBook
mount failed

[OK]


I don't understand why this happened.


fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=aed83e83-ccc6-4ecb-9ceb-e6e9a6b77aa1 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=8628f6bc-10dc-4387-bdae-78d13104b289 /home           ext3    defaults,user_xattr        0       2
# /media/Maxtor was on /dev/sdb1 during installation
UUID=3A388D2E388CEA69 /media/Maxtor   ntfs    defaults,umask=007,gid=46 0       0
# /media/MyBook was on /dev/sdc1 during installation
UUID=CE0C0B8F0C0B71AF /media/MyBook   ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
UUID=2c1b2ae0-b3e0-4133-88fc-00c0938a7df5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```



A little more info...

In Nautilus, I have my hard drives listed under the "Devices" heading in the left pane, but nothing happens when I click on my My Book listing.  Underneath "Computer" I have a mounted MyBook entry that has mysteriously added itself.  It appears to be mounted, but when I click the eject icon it says:

**Unable to unmount MyBook**
umount: /media/MyBook mount disagrees with the fstab


Edit:
A restart fixed this, but why did it happen in the first place?

---


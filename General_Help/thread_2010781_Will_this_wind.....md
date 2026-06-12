---
title: "Will this wind....?"
date: 2012-06-26
forum: General Help
---

### Post by robert shearer on 2012-06-26
Thanks for looking,...
I have a testing rig multi-booting several linux O/S' and Windows. (15 partitions total)

I now want to reduce this to Ubuntu 11.10, Windows and a new install of 12.04.

I can use Gparted to remove several partitions and create some new ones then run 
```
sudo update-grub
``` 
to recognise the new partitions to boot.

However, will the existing 11.10 install then know where Home is if Home is currently something like sda12 and after reallocating there are only  5 partitions on the drive...??
Or do the unaltered partitions retain their previous identities and Home will still be known as sda12 ???

Or how do I update the Home link...?

---

### Post by surfer on 2012-06-26
if your partitions in /etc/fstab are identified by their uuid (as they should), it should be possible to move them around on the disc (meaning: a change of the device number should not be a problem).

---

### Post by robert shearer on 2012-06-26
Looks like they are......Here is the 11.10 install I am posting from....
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=abd2e4f2-faf9-4764-8239-505f420e2048 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda12 during installation
UUID=9f67d191-be93-4e5d-ac51-39c85a894967 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=5bcbaa76-269f-47bc-bbb5-5d25ef392f3e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---


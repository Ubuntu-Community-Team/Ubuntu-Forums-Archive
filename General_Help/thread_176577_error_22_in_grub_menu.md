---
title: "error 22 in grub menu"
date: 2006-05-15
forum: General Help
---

### Post by Bubolzm on 2006-05-15
this is what i did. (total of 3 hard drives)
Hard drive #1 has windows, unplugged it.
hard drive #2 has bad ubuntu (this is what im fixing)
hard drive # 3 has good ubuntu.

hard drive 1, 2 worked well together with grub menu, but i would rather have both actually work. (xserver error)

so, i try to fix the xserver error. works. but i find i still dont have god networking plus there is tons of bad things up with it. want to reinstall.
i restart and go into windows, then i open up the disk management utility. i format both the ubuntu sections on HD#2

i shutdown, unplug HD #1 and make HD#2 master

then i reinstall, i have the same problems.

i go back  to having HD 1 as master and HD 2 as slave, but i get an error (21 or 22)

grub doesnt like it. neither do i

an hour later, i shutdown and place HD 2 as master and start up.
this time with the install cd. i install until the partitioner, i erase the ubuntu partitions. and retry windows, nothing same error 22

still happens when i have windows drive as only drive...

---

### Post by Sef on 2006-05-15
These are what the GRUB errors mean:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

Wondering if you reinstall GRUB would take care of the problem.  See if it could find the partitions.

---

### Post by confused57 on 2006-05-15
Check out this thread... it may be a matter of Grub pointing to the correct HD and partition, as mentioned near the end of the thread:

[http://www.ubuntuforums.org/showthread.php?t=176071](http://www.ubuntuforums.org/showthread.php?t=176071)

Are you able to boot into windows when it's the only drive connected?  I'm not sure what it is that you're trying to accomplish, do you plan on having all 3 drives connected at the same time, switch out cables depending on which OS you want to use?
If you need to get windows working again, you'll need to bootup with the windows install CD  and type in "fixmbr".  As Sef mentioned you may need to reinstall GRUB.   Grub needs to know where to find your OS, which drive and which partition on the drive.  This could possibly be done by editing your menu.lst &  I'm sure someone could help you if you can provide a little more information.  I'm pretty new at this, but hope this may help you find a solution.

This link may provide some useful information:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29)

---


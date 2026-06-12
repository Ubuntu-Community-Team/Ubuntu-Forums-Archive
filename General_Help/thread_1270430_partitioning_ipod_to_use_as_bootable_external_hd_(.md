---
title: "partitioning ipod to use as bootable external hd (for installing OS)"
date: 2009-09-19
forum: General Help
---

### Post by waxjism on 2009-09-19
My ipod is a 4Gb 2nd gen Nano. 

cfdisk tells me "Wrote partition table, but re-read table failed.  Reboot to update table." When I tried to write a FAT16 partition it pretended to write it but syslinux could not recognise it as valid. When I try ext2, nothing at all seems to happen. 


gparted tells me "Device /dev/sdd has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Can't have a partition outside the disk!"

and crashes as soon as I try to scan the device. 



What can I do to get a working partition on this thing?

---

### Post by marcopolo1981 on 2009-09-19
Are you trying to use the entire capacity to install the OS, or partitioning it into 2 or more seperate partitions?

I have a 20Gig Archos media player, and it will only allow me to half the original capacity. The first half MUST be FAT32 in order for the machine to not overwrite it, formatting the entire capacity again as FAT32.
The second part is to then create a logical partition or the remaining space, then create an EXT2 or EXT3 partition. (I strongly suggest that no part of the storage in these types of devices is used as SWAP. I have gone through 2 expensive hard drives very quickly with SWAP space on them!)
Once this has successfully completed, if it works at all, remove the device from the usb and check that it doesn't overwrite the partition table automatically. If it still works, maybe then try to install the OS.

Best of luck!

Mark

---

### Post by waxjism on 2009-09-19
I tried that (in cfdisk) and again, could not re-read table, and after rebooting the ipod and plugging it in again I get: 

waxjism@Jean-Luc:~$ dmesg | tail
[31327.406289] FAT: unable to read boot sector
[31327.449143] FAT: bogus logical sector size 65535
[31327.449153] VFS: Can't find a valid FAT filesystem on dev sdd1.
[31359.070691] FAT: Directory bread(block 123) failed
[31359.070715] FAT: Directory bread(block 124) failed
[31359.070737] FAT: Directory bread(block 126) failed
[31359.070752] FAT: Directory bread(block 127) failed
[31359.070769] FAT: Directory bread(block 128) failed
[31359.070784] FAT: Directory bread(block 129) failed
[31359.070799] FAT: Directory bread(block 130) failed


cfdisk shows: 

sdd1 Boot Primary W95 FAT32 698.37
sdd5  -   Logical Linux     3360.90

---

### Post by marcopolo1981 on 2009-09-19
Try deleting all partitions from the ipod completely, unmount it, remove from the pc. Then turn it off and back on (ipod that is) and see if it complains. If it shows an option to reformat itself, let it. Then try again. It may just need to refresh itself.
Not all portable devices will allow you to partition the internal storage, and this just may be one of them. Sorry I can't be of more help.

Mark

---


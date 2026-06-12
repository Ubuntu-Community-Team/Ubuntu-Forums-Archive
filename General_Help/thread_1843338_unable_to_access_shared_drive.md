---
title: "unable to access shared drive"
date: 2011-09-13
forum: General Help
---

### Post by vigeek on 2011-09-13
I am not able to access one of my partitions through ubuntu studio....though it was working earlier.The partition is still accessible from windows 7 as my system is dual boot.....that particular partition does not contain any OS..can any one help me??

---

### Post by ksprasad on 2011-09-13
Hi,
 
Please run 'sudo fdisk -l' command and see if that partition is listed there.
You can post the output of that command here.
 
Regards,
Ksprasad

---

### Post by vigeek on 2011-09-13
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000abd81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              13        3825    30617600    7  HPFS/NTFS
/dev/sda2   *        3825        5697    15039488   83  Linux
/dev/sda3            5698       38914   266809345    f  W95 Ext'd (LBA)
/dev/sda5            7281       38396   249939238+   7  HPFS/NTFS
/dev/sda6           38397       38914     4154368   82  Linux swap / Solaris
/dev/sda7            5698        7280    12715008   83  Linux

---

### Post by ksprasad on 2011-09-13
Is that partition NTFS? Is it listed above? If its sda5, then you can try mounting it manually,
 
sudo mount -t ntfs /dev/sda5 <mount point>
 
Here, mount point is any directory where you want to mount the partition. Give any empty existing directoy such as ~/mount_dir

---

### Post by vigeek on 2011-09-13
it was already mounted in shared directory....but now when i try to open it says......permission denied......and i cant access that drive

---

### Post by ksprasad on 2011-09-13
Give nautilus root [FONT=Calibri]privilege.[/FONT]
```

gksudo nautilus

```
 
I think now you can access that drive.

---

### Post by vigeek on 2011-09-14
thanx alot.....solved the problem  :)

---

### Post by ksprasad on 2011-09-14
Great to hear that :) Cheers

---

### Post by vigeek on 2011-09-15
but its not permanent......i have to give root permissions again n again....after sometime...its unacessible n i have to type the command..moreover i cant access that drive to save files in browsers..or load music folders in music player library

---


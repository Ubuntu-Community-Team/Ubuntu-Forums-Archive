---
title: "USB pen drive no longer getting detected"
date: 2010-02-13
forum: General Help
---

### Post by arjunak01 on 2010-02-13
i have a kingston 4GB pen drive. it used to work with ubuntu, but now ubuntu is no longer able to detect it.Gparted is also not detecting it. here is the output of **lsusb**

[I]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0c45:607c Microdia CCD PC Camera (PC390A)
Bus 003 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

and that of **sudo fdisk -l **

[I]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    c  W95 FAT32 (LBA)
/dev/sda2            1306        7832    52428127+  83  Linux
/dev/sda3            7833       28780   168264810    5  Extended
/dev/sda4           28781       30401    13020682+  83  Linux
/dev/sda5            7833       27413   157284351    7  HPFS/NTFS
/dev/sda6           27414       28718    10482381    b  W95 FAT32
/dev/sda7           28719       28780      497983+  82  Linux swap / Solaris[/I]

---

### Post by rocket16 on 2010-02-13
Hello Arjuna, me too from India! :)

By the way, try accessing the Drive after using the command "sudo nautilud" to open a Root-explorer. And, is the partition of your drive NTFS? If so, try to reformat ot to FAT16 using Windows OS, if you have any.

---

### Post by NE Key on 2010-02-13
Plug it in and then use the disc utility  - Menu> System Administration>Disk Utility -  to examine and repair.

---


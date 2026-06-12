---
title: "Ubuntu 8.04 Doesn't Detect USB Flash Drive - Please Help"
date: 2011-02-03
forum: General Help
---

### Post by Heliophion on 2011-02-03
The hard drive on my desktop recently failed, so I ended up getting a new computer. I put a fresh install of Ubuntu 8.04 on the new computer but it doesn't auto-detect my USB flash drives. They only show up if I plug them in and then type 'lsusb' in terminal. Have been using Ubuntu since 6.06. My previous system, using the same 8.04 release, simply auto-detected the drives when I plugged them in. This is not the case with the new system. I've included the terminal messages below. Any help would be appreciated. 

```
 lsusb

Bus 005 Device 004: ID 154b:0041  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 001 Device 005: ID 04b3:301a IBM Corp. 
Bus 001 Device 004: ID 04b3:310c IBM Corp. 
Bus 001 Device 001: ID 0000:0000  

```

```
 sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000628a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    c  W95 FAT32 (LBA)

```

---

### Post by Heliophion on 2011-02-03
Anyone?

---


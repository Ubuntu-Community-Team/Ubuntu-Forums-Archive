---
title: "External hdd unable to mount"
date: 2010-02-12
forum: General Help
---

### Post by hairypreacher on 2010-02-12
Hello, 
I've had a look around the forums but cant seem to find the answer. 

I have a brand new external iomega hdd, when i plug it in i get the message 

Unable to mount the volume 'Iomega HDD'. 

and this...

$logfile indicates unclean shutdown (0,0) failed to mount '/dev/sdb1': operation not supported mount is denied because NTFS is marked to be in use chose one actio....
the first is for windoze the second says if you dont have windows you can use the 'force' option.

In teminal i get the follwing

lsusb: 
Bus 004 Device 005: ID 059b:0370 Iomega Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

sudo fdisk -l
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0455efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14830   119121943+  83  Linux
/dev/sda2           14831       15017     1502077+   5  Extended
/dev/sda5           14831       15017     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27e9bfe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

If I try the hdd on my brothers fedora pc it works straight away and even on windoze 7.

My System is 8.04 (hardy) 2.6.24-27-generic, Gnome 2.22.3

I want to back up my data before i upgrade to 9.10 :)

Many thanks
Andy

---

### Post by sandyd on 2010-02-12
> **hairypreacher said:**
> Hello, 
I've had a look around the forums but cant seem to find the answer. 

I have a brand new external iomega hdd, when i plug it in i get the message 

Unable to mount the volume 'Iomega HDD'. 

and this...

$logfile indicates unclean shutdown (0,0) failed to mount '/dev/sdb1': operation not supported mount is denied because NTFS is marked to be in use chose one actio....
the first is for windoze the second says if you dont have windows you can use the 'force' option.

In teminal i get the follwing

lsusb: 
Bus 004 Device 005: ID 059b:0370 Iomega Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

sudo fdisk -l
Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0455efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14830   119121943+  83  Linux
/dev/sda2           14831       15017     1502077+   5  Extended
/dev/sda5           14831       15017     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27e9bfe8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

If I try the hdd on my brothers fedora pc it works straight away and even on windoze 7.

My System is 8.04 (hardy) 2.6.24-27-generic, Gnome 2.22.3

I want to back up my data before i upgrade to 9.10 :)

Many thanks
Andy```

sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdb1 /media/external -o force
```

---

### Post by hairypreacher on 2010-02-12
Thankyou carlee, 
All working now :D

---

### Post by EPurpl3 on 2010-02-13
Wow, thx, worked for me too.

---

### Post by arno77 on 2010-02-23
Worked perfect for me too. THANKS!

---


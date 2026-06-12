---
title: "Mounting Issues"
date: 2012-02-02
forum: General Help
---

### Post by rheugle on 2012-02-02
My computer shut down and when I tried to reboot, I got a bunch of RAID error messages. I booted off a CD rom and am trying to mount my old files in a new folder. 

When i use fdisk, I can see sda1, sda2, sdb1, sdb2, etc. But when I go into DEV and ls, all I see is sda and sdb. It seems Linux isn't recognizing my partitions. 

Can anyone suggest how to proceed?

Thanks!

---

### Post by BC59 on 2012-02-02
Try installing the Storage Device Manager from Ubuntu Software Center. Then open it and set all the partitions to default.

---

### Post by rheugle on 2012-02-02
Hi 

Thanks for the reply. That doesn't seem to work. The partition list in the Storage Device Manager only lists sda and sdb. Refreshing doesn't seem to help either. 

FYI, this is what fdisk -l looks like:

root@ubuntu:/dev# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  fd  Linux raid autodetect
/dev/sda2            9727       27962   146480670   fd  Linux raid autodetect
/dev/sda3           27963       30394    19535040   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9726    78124063+  fd  Linux raid autodetect
/dev/sdb2            9727       27962   146480670   fd  Linux raid autodetect
/dev/sdb3           27963       30394    19535040   fd  Linux raid autodetect

---

### Post by BC59 on 2012-02-02
In Device Manager, on the left panel, they are listed the partitions. You have to push on sda and sdb to deploy them.

---

### Post by rheugle on 2012-02-02
I have been, it doesn't seem to help at all. Clicking on either sda or sdb and then clicking apply doesn't help at all. Also, no other options are available for me in the SDM. 

Any other lines of attack?

---


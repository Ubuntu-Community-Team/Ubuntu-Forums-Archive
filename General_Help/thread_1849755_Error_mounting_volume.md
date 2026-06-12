---
title: "Error mounting volume"
date: 2011-09-25
forum: General Help
---

### Post by Bote on 2011-09-25
Hello,

I'm a little bit new to ubuntu and I just installed it on my pc. I have 4 harddrives, 3 of them are working great. the last one isn't. 

If I go to places and select him I get this:
Unable to mount New Volume
Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sda1 on media/sda1

I tried to format it but it didn't help.

If someone could help me, it would be great.

Thibault Heylen

---

### Post by agillator on 2011-09-25
At first glance it appears that you are trying to mount it as a normal user which isn't going to work without tweaking, which you probably don't want to do. So, assuming the partition /dev/sda1 is mountable, go to System | Administration | Disk Utility and select that drive if it is listed. If it is not listed you have other problems. Note the file system type of sda1. Try mounting it with this utility. If that works, then close the Disk Utility. In the future to mount it you would open a terminal and enter 'sudo mount -t <fs type> /dev/sda1 /mnt/sda1'. This assumes, of course, that /mnt/sda1 exists. To mount it automatically when you boot you would put an entry in /etc/fstab - just follow the format of the others that are in there.

---

### Post by ajgreeny on 2011-09-25
I don't know which version of ubuntu you are running, but in all up to, and possibly including 11.04, there is an applet for the panel called Disk-mounter which can be very useful.  Have a look for that.

---

### Post by Bote on 2011-09-25
Thank you for the response:
@ agillator:
If I go to Disk Utility I can see my harddrive. If I press Mount volume I get this error:
Error mounting volume
An error occured while performing an operation on "NewVolume"(Partition 1 of ATA ST375084AS): The operation has failed

details:
Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sda1 on /media/sda1

so even mounting doesn't work

@ajgreeny:
I run Ubuntu 11.04. I added Disk-mounter in my panel but when I press that harddisk I choose mount but nothing happens

---

### Post by ajgreeny on 2011-09-25
Please show the output from command ```
sudo fdisk -l
```

---

### Post by Bote on 2011-09-25
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf81bf81b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f34e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      250880   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32       19458   156037121    5  Extended
/dev/sdb5              32        1004     7811072   82  Linux swap / Solaris
/dev/sdb6            1005       10123    73241600   83  Linux
/dev/sdb7           10123       19458    74982400   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17f8a47c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121602   976761528+  42  SFS

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x994f51cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdf: 16.0 GB, 16013852672 bytes
78 heads, 14 sectors/track, 28641 cylinders
Units = cylinders of 1092 * 512 = 559104 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           8       28642    15634496    c  W95 FAT32 (LBA)


It's about that first disk (750GB)

---

### Post by raja.genupula on 2011-09-25
up to your problem gonna resolve , you can mount your partition from terminal .this is a temporary solution to you .

```
sudo mount /dev/sda1 /media
```

actually for this types of problems sometimes your GDM also going to be a cause.so please try to do update of your system.

All The Best.

---

### Post by ajgreeny on 2011-09-25
Raja's command should mount the partition, if it can be mounted, but can we also see the output of ```
sudo blkid
``` and ```
cat /etc/fstab
```please.

---

### Post by Bote on 2011-09-26
This must sound very stupid but I booted my system and I can acces my hard drive...
I don't know how it was possible but suddenly it worked...
I will keep your advice for next time when it should fail again...

thank you for the help thoug

---

### Post by ajgreeny on 2011-09-26
Great!  Can you mark your thread as solved from the **Thread Tools** menu at the top, please.

---

### Post by mrnatas20 on 2012-04-11
If it helps anyone in the future, after first trying to open Disk Utility and failing because it didn't have sudo permissions, I found the binary name to be "palimpsest", so running ```
sudo palimpsest
``` allowed the Disk Utility to mount the volume.

---


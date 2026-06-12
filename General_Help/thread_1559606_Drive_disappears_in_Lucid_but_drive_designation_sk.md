---
title: "Drive disappears in Lucid but drive designation skipped"
date: 2010-08-23
forum: General Help
---

### Post by MindSpasm on 2010-08-23
I have only been using Ubuntu since shortly after Lucid was released. I am a new convert and use it to run a back-up device / media server.  I have a total of 5 hard drives in the device. 

They should be as follows. 
/dev/sda (SATA WD EARS 2TB)
/dev/sdb (SATA WD EARS 2TB)
/dev/sdc (SATA WD EARS 2TB)
/dev/sdd (SATA WD EARS 2TB)
/dev/sde (IDE Maxtor 40GB)

I have the Lucid system files written to /dev/sde. I am running a Raid 1 array with mdadm on /dev/sdc and /dev/sdd. I have been prepping to run a second raid 1 array with /dev/sdb and /dev/sda with the ext4 file system. I formatted /dev/sda to have a full partition of /dev/sda1. I then went to do the same to /dev/sdb and the drive was missing from both gparted and the native disk utility. My array with sdc and sdd is still running with both drives working fine. I swapped the sata cable from sda and sdb with no change. The system will not recognize sdb no matter what I do but it does skip /dev/sdb in boot up which tells me it does see it.  


Is there any information that someone here can provide to give an explanation of this? 

I have provide the output of the commands df, fdisk -l, and cat /proc/mdstat.  

If there is anything else needed then please feel free to ask, your assistance is greatly appreciated. 

```

dave@Deathstar:~$ uname -a
Linux Deathstar 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
dave@Deathstar:~$ 



Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sde1             36843088  12986620  21984904  38% /
none                   1508380       324   1508056   1% /dev
none                   1513016      1296   1511720   1% /dev/shm
none                   1513016       340   1512676   1% /var/run
none                   1513016         0   1513016   0% /var/lock
none                   1513016         0   1513016   0% /lib/init/rw
/dev/md0             1953514492 661354580 1292159912  34% /media/Back_Ups


dave@Deathstar:~$ fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b384f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdd4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/md0: 2000.4 GB, 2000398843904 bytes
2 heads, 4 sectors/track, 488378624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1   ?      822447   240553456   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not end on cylinder boundary.
/dev/md0p2   ?   244156454   471478443   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/md0p3   ?    28216909    28216910           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/md0p4       330301441   330307927       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000140d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        4661    37431296   83  Linux
/dev/sde2            4661        4866     1648641    5  Extended
/dev/sde5            4661        4866     1648640   82  Linux swap / Solaris
dave@Deathstar:~$ 


dave@Deathstar:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd[0] sdc[1]
      1953514496 blocks [2/2] [UU]
      
unused devices: <none>
dave@Deathstar:~$ 


```

---

### Post by MindSpasm on 2010-08-24
Help Please! :) I don't want to risk losing any further data from other drives doing the same.

---

### Post by MindSpasm on 2010-08-28
I fixed my own issue.  Thinking that the port on the motherboard might have fried itself, I purchased a new motherboard for my system. Since the drive was down and I wasn't able to utilize that part of my system, I hooked the drive into a dock on my windows 7 machine and  attempted a re-format to ntfs. When I tried to format as a MBR drive it failed even on the windows machine so I formatted it as a GUID partition table. I was then able to move it back to the server and format it to MBR with ext4 with no problems. I have also been able to create my second Raid Array running on this box using MDADM. 

On a side note,  I changed from an IDE 40 gig to a 160 gig sata as my primary drive for system files. I found that after installing my Ubuntu on the new drive,  I could not get past a blinking cursor when booting up after the initial install.  I found the solution in moving the drive I was installing to from sde to sda and did a clean install to that drive. After I did so I had no issues getting the system up and running. I would guess that my system wasn't finding Grub even though I had only that drive selected as the boot drive in bios. 

Thanks for the help, Oh wait there were no messages of assistance here. The community based help does not seem to be there like was touted to me which made me desire to even attempt another linux install.   We shall see how it goes now. 

I do hope that someone finds this information useful in the future.   Have a great day.

---


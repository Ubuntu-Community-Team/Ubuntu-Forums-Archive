---
title: "XP is killing my data, filesystem problems"
date: 2009-09-21
forum: General Help
---

### Post by The Real Dave on 2009-09-21
Ok, so upon re-installing XP, I get an error, saying a certain file cannot be copied. Its a file on a floppy disk, a driver for my harddrive. I reboot, into a live CD, and somethings wrong. Before the install, my drive setup was like this

-Extended
----Root Ubuntu
----Home
----Swap
-Windows XP (old install)
-XP (fat32 partition for new install)
-Data (fat32)

Now, that data partition shows up as unpartitioned space in the Windows setup, and gparted shows the whole 300Gb drive as being unpartitioned, but its not, as I can still get access to every partition bar the Data drive, which doesn't appear at all. I think its worth mentioning that during the install I selected that Windows should reformat the XP fat32 partition to NTFS. I definately selected that partition, I triple checked it. 

Fdisk from the live cd is as follows 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67df67df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10011    80413326   83  Linux
omitting empty partition (5)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009628c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+   5  Extended
/dev/sdb2            6248        6374     1020096   82  Linux swap / Solaris
/dev/sdb3   *        6375        9548    25495155    c  W95 FAT32 (LBA)
/dev/sdb4            9549       12748    25704000    7  HPFS/NTFS
/dev/sdb5               1        1147     9213183   83  Linux
/dev/sdb6            1148        6247    40965718+  83  Linux
ubuntu@ubuntu:~$ 
```

I read that you can convert a fat32 partition to NTFS without losing data, but I can't do that, as I have no partition there anymore, it appears as unpartitioned space. Also, GParted no longer sees anything. Can someone please help me make a new partition in that unpartitioned space, without formatting it, because every drop of my data is on there, 100+Gb. Any help is greately appreciated

---

### Post by louieb on 2009-09-21
Not time to panic you just need to stop and think things through. 

XP did ot kill your data but the install sure messed up the partition table.
For some reason swap is now primary and inside extended partition sdb1.

And theres a large chunk of unallocated space starting at cylinder 12749 - to the end of disk. As it now it can't be allocated to a partition. 

Because of sda2 being inside sda1 - Gparted treats the disk as empty 

testdisk should  be able to change sda2 into a logical partition. freeing up sda2 to be used later to create a primary partition. Thats the 1st thing I would do.   

After that is done the testdisk should be able to assign  the unallocated space to sda2. Need to be careful here wonder if the original data partition started at cylinder 9549 or 12749?  


That Recommend you get a recovery CD like SystemRescue or PartedMagic. Either will have the latest version of the programs you will need. 


```

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, [COLOR=Sienna]38913 [/COLOR]cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009628c

   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        [COLOR=Red]6374[/COLOR]    51199123+   5  Extended
/dev/sdb5               1        1147     9213183   83  Linux
/dev/sdb6            1148        6247    40965718+  83  Linux
/dev/sdb2            6248        [COLOR=Red]6374[/COLOR]     1020096   82  Linux swap / Solaris
/dev/sdb3   *        6375        9548    25495155    c  W95 FAT32 (LBA)
/dev/sdb4            9549       [COLOR=Sienna]12748  [/COLOR]  25704000    7  HPFS/NTFS

```

---

### Post by pcjunkie on 2009-09-21
Convert format: Not sure on the process in Linux but I would say it can be done. Casper disk imaging can easily convert FAT to NTFS so I would Imagine someone will know how to do this in Linux.

---

### Post by The Real Dave on 2009-09-21
Using testdisk, I managed to recover the Data partition, the last one, but seem to have lost the Home and Root partitions in the process. I'm doing a deeper scan now to recover these. Thanks a million to the posters for the help and ideas

---


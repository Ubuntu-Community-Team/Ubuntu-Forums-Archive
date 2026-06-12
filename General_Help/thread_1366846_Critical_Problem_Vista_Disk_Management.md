---
title: "Critical Problem: Vista Disk Management"
date: 2009-12-28
forum: General Help
---

### Post by haribol707 on 2009-12-28
hello,

I have a dual-boot system with ubuntu 9.04 and vista ultimate. Couple of days back, I used the Vista Disk Management util:

ity to shrink my existing drive (C:) and create a new drive from the freed up space. I was able to shrink the drive and get ~16GB free space. Next, I selected the unallocated space and chose 'Create Simple Drive' option to create a new drive. It gave me a dialog stating '<something> will be changed to Dynamic type'. I chose 'Yes' and let it continue. Basically, it said it would create a dynamic disk (I was not aware of Basic/Dynamic types until I ran into trouble). 
Problem 1: The drive creation failed. It gave an error message "File not found". I chose to restart the system.
Probelm 2: Upon reboot, GRUB failed with error 22. With a bit of googling (Ubuntu LiveCD came in handy), I figured it to be corrupted mbr. As a soln, I put in my Vista DVD and created new MBR by executing their Bootrec.exe cmd. (bootrec /<>Mbr)
Problem 3: With GRUB gone, I was able to boot into Vista directly. But the file explorer in vista was now showing my Linux drives (root and swap). (Disk mgmt showed it as Healthy, Raw format). I was puzzled as Vista never shows Linux partitions in File Explorer. I went ahead and converted the unallocated space into a new drive (NTFS).
Problem 4: I rebooted again and this time used Ubuntu Live. Gparted showed a different picture of the harddisk altogether!
Originally, the partitions were like this:

Linux root: 10GB
Swap: 2GB
Windows C: : 110GB
New Partion: 18GB
Hp recovery (active): 16GB

However, Gparted showed this information:

sda1: ext3, 11.5GB (possibly linux + swap?)
sda2: ntfs: 105.12GB
sda3: unknown 16.68GB
sda4: ntfs 16GB (this is the new partition I created)

I am confused by gparted's display here. Looks to me like the partition table is corrupted? Please let me know how I can solve this issue with minimal damage (OS reinstall). 

Right now, I am able to use Vista, but cannot log into Linux.

Also, fdisk -l shows all the partitions as SFS file system types. Is this problem caused by Vista converting my drives to dynamic? How do I prevent Vista from setting drives as Dynamic in future? 

fdisk -l:

```


======================
root@ubuntu:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff9f16c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1490    11961312+  42  SFS
/dev/sda2            1490       15212   110226428   42  SFS
/dev/sda3           15212       17389    17489370+  42  SFS
/dev/sda4   *       17390       19457    16611210   42  SFS


```


parted list all:

```

odel: ATA WDC WD1600BEVT-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  12.2GB  12.2GB  primary  ext3              
 2      12.2GB  125GB   113GB   primary  ntfs              
 3      125GB   143GB   17.9GB  primary                    
 4      143GB   160GB   17.0GB  primary  ntfs         boot 


```

---

### Post by conradin on 2009-12-31
BUMP! 
HI all, I'm having pretty much the same issue with windows dynamic disk and this SFS file system. Ive preused the archives a little and not found a solution. My only thought is to open the dynamic disk from windows and try to copy everything on it to a disk formated with a different file system (like NTFS). 

Is there any program or anyone that can help Ubuntu users deal with dynamic disks? HELP Please!:confused:

---


---
title: "Problem Adding a Partition"
date: 2009-09-29
forum: General Help
---

### Post by sarloth on 2009-09-29
Hey guys, I think the terminal output will basically explain it, but I am having some issues adding a partition. I recently deleted a partition in the place this one will reside and now I cannot add a new one, and am getting "Can't have overlapping partitions". 

Gparted isn't an option as this is a server install and I am working on it from SSH.

Any advice would be much appreciated. I am trying to get rid of the NTFS partition but at the moment it is full of important data and I do not have another drive large enough to hold it. The plan is to add a partition in the available space, make that a a Physical Volume and add that to an already created LVM.

```

GNU Parted 1.8.8
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) select /dev/sdb                                                  
Using /dev/sdb
(parted) print                                                            
Model: ATA ST3200822A (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  50.0GB  50.0GB  extended                    
 5      64.5kB  50.0GB  50.0GB  logical                lvm  
 1      50.0GB  120GB   70.1GB  primary   ntfs         boot 

(parted) print free                                                       
Model: ATA ST3200822A (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  50.0GB  50.0GB  extended                    
 5      64.5kB  50.0GB  50.0GB  logical                lvm  
 1      50.0GB  120GB   70.1GB  primary   ntfs         boot 
        120GB   200GB   79.9GB            Free Space        

(parted) mkpart logical 120GB 200GB
Error: Can't have overlapping partitions.                                 
(parted) mkpart logical 130GB 200GB                                       
Error: Can't have overlapping partitions.                                 
(parted) mkpart logical 150GB 200GB                                       
Error: Can't have overlapping partitions.                                 
(parted) mkpart logical 175GB 200GB                                       
Error: Can't have overlapping partitions. 

```

---

### Post by korin43 on 2009-09-29
Why not use fdisk? If you save the configuration how it is and add a partition with fdisk, the default will be to fill all remaining space (which seems to be what you want to do). It would be something like "fdisk /dev/sdb". "p" will list partitions. "n" creates a new one.

---

### Post by sarloth on 2009-09-29
> **korin43 said:**
> Why not use fdisk? If you save the configuration how it is and add a partition with fdisk, the default will be to fill all remaining space (which seems to be what you want to do). It would be something like "fdisk /dev/sdb". "p" will list partitions. "n" creates a new one.

Thanks for the suggestion. However:

```

The number of cylinders for this disk is set to 24321.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02268bf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        6081       14608    68501160    7  HPFS/NTFS
/dev/sdb2               1        6080    48837568+   5  Extended
/dev/sdb5               1        6080    48837537   8e  Linux LVM

Partition table entries are not in disk order

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
l
No free sectors available


```

I think that is scarier.

---

### Post by sarloth on 2009-09-29
Anyone reading this isn't going to believe this sh-- but evidently it had to be a primary partition.....

```

GNU Parted 1.8.8
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA ST3200822A (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  50.0GB  50.0GB  extended                    
 5      64.5kB  50.0GB  50.0GB  logical                lvm  
 1      50.0GB  120GB   70.1GB  primary   ntfs         boot 

(parted) mkpart primary 120GB 200GB                                       
(parted) print                                                            
Model: ATA ST3200822A (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      32.3kB  50.0GB  50.0GB  extended                    
 5      64.5kB  50.0GB  50.0GB  logical                lvm  
 1      50.0GB  120GB   70.1GB  primary   ntfs         boot 
 3      120GB   200GB   79.9GB  primary   ext4          

```

Now to see if it will work for an lvm.

---


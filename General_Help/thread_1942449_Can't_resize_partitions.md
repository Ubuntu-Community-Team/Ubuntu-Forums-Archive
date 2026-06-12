---
title: "Can't resize partitions"
date: 2012-03-17
forum: General Help
---

### Post by Crowchild on 2012-03-17
Help!

    I'm trying to shrink my extended partition (where ubuntu is installed) so I can grow my primary partition to allow for more space for my Windows 7 install. When I try to do the first step with gparted I get a message that this would cause overlapping partitions?!

---

### Post by oldfred on 2012-03-17
May be best to post a screenshot from gparted of your drive.

You have to shrink a partition inside the extended and then move partition (good backups important) so free space is at beginning. 

You may be able just to shrink the Linux partition and create a shared NTFS data partition inside the extended if all you need is more room for data? That would be a bit less risky than moving partitions around.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Crowchild on 2012-03-17
The unallocated space is at the start of the extended partition. When I try to shrink that partition I get the message:

GParted 0.8.1 --enable-libparted-dmraid

Libparted 2.3
Move /dev/sda3 to the right and shrink it from 78.85 GiB to 65.13 GiB  00:00:00    ( ERROR )
     	
calibrate /dev/sda3  00:00:00    ( SUCCESS )
     	
path: /dev/sda3
start: 80584702
end: 245940223
size: 165355522 (78.85 GiB)
move partition to the right and shrink it from 78.85 GiB to 65.13 GiB  00:00:00    ( ERROR )
     	
old start: 80584702
old end: 245940223
old size: 165355522 (78.85 GiB)
libparted messages    ( INFO )
     	
Can't have overlapping partitions.

========================================

---

### Post by oldfred on 2012-03-17
Were drives ever set to RAID?

Post this:

sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

And back up partition table just in case.

First backup partiton table, use your drive for  sda, sdb etc.
sudo sfdisk -d /dev/sda > parts_sda.txt

---


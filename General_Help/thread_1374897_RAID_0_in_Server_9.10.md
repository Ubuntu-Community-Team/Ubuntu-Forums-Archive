---
title: "RAID 0 in Server 9.10"
date: 2010-01-07
forum: General Help
---

### Post by omsoni on 2010-01-07
I am new to ubuntu or Linux. I got a new Dell PowerEdge to move my hosted website inhouse. It has three 160GB disks. I am installing RAID 0 on it. This is how I have planned it.
 
Disk1 : 16 GB for root partition (bootable): 144 for RAID 0 (ext4)
Disk2 : 16 GB for swap(RAM is 4 GB but will upgrade in near future) 144 for RAID 0 (ext4)
Disk3 : 16 GB for home 144 for RAID 0 (ext4)
 
Now This is my only server. I am installing LAMP.
I have already decided on RAID 0 for performance reasons.
 
Please advise.
 
On size and type of my partitions.
Any other considerations related to MySQL for these partitions.
I do plan on adding more servers in future. Anything I need to consider in terms for partitions for that.
 
 
Thanks for all the help

---

### Post by tgalati4 on 2010-01-11
16 gb of swap is excessive.  2 to 4 gb is sufficient.  Use smartmontools to get the power-on hours of the disks.  If greater than 30k get new disks.

---


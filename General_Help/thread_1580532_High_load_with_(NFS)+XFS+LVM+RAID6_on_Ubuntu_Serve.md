---
title: "High load with (NFS)+XFS+LVM+RAID6 on Ubuntu Server 10.04"
date: 2010-09-23
forum: General Help
---

### Post by MetaYii on 2010-09-23
I have a Xeon server with 16 Gb RAM and a RAID6 on a LSI MegaRaid 84016E card, consisting in 7 x 2Tb SATA II drives, and on the same card a RAID1 with 2 x 500 Gb SATA II drives.

The RAID1 is used for operating system (Ubuntu Server 10.04 LTS) and some minor NFS shares. The partition I tested is a XFS one, mounted with defaults.

The RAID6 is used as file storage for a farm, via NFS. It is a whole volume, using XFS mounted with defaults on top of LVM. 

The problem is this: under relative high I/O, either local (bonnie++ -r 8000 -s 16000 -u root) or real world via NFS, the  load goes way high (9-12 on average) when testing the RAID6 volume. Since both bonnie++ and normal NFS I/O increases the load, I assume NFS is not guilty here. So my main suspect is LVM.

Just for comparation: testing with the same bonie++ command on the XFS on RAID1 volume, the load goes just up to 1 or 2.

In both cases, CPU usage is nearly 10% per thread (core, as seen by htop) in the quad-core-eight-thread Xeon.

I've (maybe too late :mad:) read about kernel and load problems with setups similar to mine:

[http://www.mysqlperformanceblog.com/2009/02/05/disaster-lvm-performance-in-snapshot-mode/](http://www.mysqlperformanceblog.com/2009/02/05/disaster-lvm-performance-in-snapshot-mode/)

[http://www.mysqlperformanceblog.com/2010/05/18/is-your-servers-performance-about-to-degrade/#comment-765400](http://www.mysqlperformanceblog.com/2010/05/18/is-your-servers-performance-about-to-degrade/#comment-765400) 

[https://bugzilla.redhat.com/show_bug.cgi?id=240077](https://bugzilla.redhat.com/show_bug.cgi?id=240077)

So, I have some questions:

1) Has anyone experienced similar problems with XFS on LVM with modern Ubuntus?
2) Could it be a fault of the RAID6?
3) How can I delete a LVM volume without rebooting the server, in order to create a physical partition with XFS on it? (I can move the data to another partition and then umount the XFS fs)

Thanks in advanced.

---


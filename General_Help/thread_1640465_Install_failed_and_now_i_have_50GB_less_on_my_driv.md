---
title: "Install failed and now i have 50GB less on my drive, a partition disappeared"
date: 2010-12-07
forum: General Help
---

### Post by jorgeguberte on 2010-12-07
Hi.
I tried to install Ubuntu 10.10 from the live cd. Everything went smooth up to the point where it told me it couldnt keep on going, right when i saw the map so i could set the timezone. 
Ok...by then i was seeing the whole hard disk with two partitions. I rebooted to Windows and then i saw i had 50GB less on the hard drive. Now i`m on the live session on Ubuntu desperately trying to find the missing partition, but got no clue regarding what to do.
I want to delete the partition, get the 50GB back on Windows and try to install Ubuntu again, without formatting the drive.

Thanks in advance.


EDIT
Nevermind, the whole drive is gone. I found the 50GB partition, deleted it and the whole drive is now empty. :(


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by oldfred on 2010-12-08
You can try testdisk.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---


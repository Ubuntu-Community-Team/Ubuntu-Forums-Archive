---
title: "Please help th is poor noob understand df output"
date: 2011-11-22
forum: General Help
---

### Post by molipha on 2011-11-22
Hi,

I'm trying to see how much space is left on my pen drive so I ran the command df -h. Here is the output:

Filesystem            Size  Used Avail Use% Mounted on
/cow                  3.0G   62M  2.8G   3% /
udev                  1.5G  4.0K  1.5G   1% /dev
tmpfs                 578M  772K  578M   1% /run
/dev/sdb1             3.8G  3.8G  9.9M 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
tmpfs                 1.5G  8.0K  1.5G   1% /tmp
none                  5.0M     0  5.0M   0% /run/lock
none                  1.5G  1.2M  1.5G   1% /run/shm

Can someone help me interpret this? FYI, ubuntu is installed on the pen drive which has 4GB capacity. The label, I believe, is PENDRIVE. 

Many thanks.

---

### Post by wyliecoyoteuk on 2011-11-22
the 4 figures in each line are the size, used, available, and free.

Filesystem Size Used Avail Use% Mounted on
/cow 3.0G 62M 2.8G 3% /
udev 1.5G 4.0K 1.5G 1% /dev
tmpfs 578M 772K 578M 1% /run
/dev/sdb1 3.8G 3.8G 9.9M 100% /cdrom
/dev/loop0 668M 668M 0 100% /rofs
tmpfs 1.5G 8.0K 1.5G 1% /tmp
none 5.0M 0 5.0M 0% /run/lock
none 1.5G 1.2M 1.5G 1% /run/shm

The filesystem used on a usb stick is called copy on write (cow)
essentially the OS runs in RAM, and copies any file writes to the usb stick.

so /cow is 3.0G, 62M used, 2.8G available, 3% used

/dev/sdb1 lists the partitions.

USB sticks are usually cdrom filesystems

rofs is read only, shm is shared memory , and so on

---


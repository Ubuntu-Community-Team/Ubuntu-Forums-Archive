---
title: "Ubuntu Partition Shows &quot;unallocated&quot; - Need Help"
date: 2010-12-04
forum: General Help
---

### Post by carr011 on 2010-12-04
On start up, with dual boot Win 7 and 10.04, got "grub rescue>" error. With live cd, gparted shows sda1, sda2, sda3 (all for Win 7),sda4 extended 225gb, unallocated 217gb, and sda5 linux-swap 8gb. If I use the install feature of live cd, the partition set-up shows my entire ubuntu partition as free space. Attempted to mount sda4 (grub2 chroot tutorial) and got:

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
mount: you must specify the filesystem type

What happened? Been using 10.04 without issue for months. Is my Ubuntu partition recoverable?

---

### Post by Ad@m on 2010-12-04
It seems like your ubuntu partition has been erased, that is why it shows up as unallocated and free space.

What did you do to cause this?

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by efflandt on 2010-12-04
From live CD what shows for output of: **sudo fdisk -l** (small L)?  Does output of that or **sudo fdisk -lu** show any partitions overlapping or in wrong order?

If you paste that here, wrap code tags around it to preserve formatting by highlighting that text and clicking **#** in top of message window.

---

### Post by carr011 on 2010-12-04
My daughter attempted to boot to Windows 7 but tabbed to the Vista loader(?) line instead of the Win 7 line. That's all. Can't boot to either OS now and Ubuntu is missing. I believe I will have to reinstall 10.04 to remedy?

---

### Post by carr011 on 2010-12-04
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15357116   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1913        6483    36708352    7  HPFS/NTFS
/dev/sda3            6483       31342   199680000    7  HPFS/NTFS
/dev/sda4           31343       60801   236629417+   5  Extended
/dev/sda5           59769       60801     8297572+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    30716279    15357116   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    30717952   104134655    36708352    7  HPFS/NTFS
/dev/sda3       104134656   503494655   199680000    7  HPFS/NTFS
/dev/sda4       503509230   976768064   236629417+   5  Extended
/dev/sda5       960172920   976768064     8297572+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by amedac on 2010-12-04
> Can't boot to either OS now and Ubuntu is missing

You can recover everything easily. Partition Table is broken, so you must recover it. The Best program for this is testdisk, search on youtube, you have step by step video tutorial.

Here is link: [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Here is tutorial: 
[http://www.youtube.com/watch?v=EncqYP1ijFg]("http://www.youtube.com/watch?v=EncqYP1ijFg")

---

### Post by carr011 on 2010-12-04
> **amedac said:**
> You can recover everything easily. Partition Table is broken, so you must recover it. The Best program for this is testdisk, search on youtube, you have step by step video tutorial.

Here is link: [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Here is tutorial: 
[http://www.youtube.com/watch?v=EncqYP1ijFg]("http://www.youtube.com/watch?v=EncqYP1ijFg")

How do I use testdisk with live cd? It is not located in the package manager and downloading and installing the .tar keeps denying me due to admin rights.

---

### Post by oldfred on 2010-12-04
It is in synaptic and on almost all Linux based repair/recovery Cd.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---


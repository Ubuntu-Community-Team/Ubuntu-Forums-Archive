---
title: "Filesystem confused about external HDD after upgrading to 10.04"
date: 2010-05-07
forum: General Help
---

### Post by tt9024 on 2010-05-07
After upgrading to 10.04, I noticed that the filesystem seems to be confused about my external HDD, which is connected via USB and called SEA_DISK. 

I am dual-booting with Windows XP, and SEA_DISK is a Windows-formatted drive.  All its files and folders look and work just fine from the Windows side.  I ran chkdsk /F and it completed normally.

On the ubuntu side, after upgrading to 10.04, notice that /media now contains a directory called SEA_DISK and one called SEA_DISK_ :

tim@bluemonster2:~$ ls -l /media
total 48
lrwxrwxrwx  1 root root     6 2008-05-03 07:50 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-05-03 07:50 cdrom0
drwxr-xr-x  2 root root  4096 2008-05-03 07:50 cdrom1
lrwxrwxrwx  1 root root     7 2008-05-03 07:50 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-05-03 07:50 floppy0
drwx------  3 tim  root  4096 2010-05-04 11:10 SEA_DISK
drwx------ 17 tim  tim  32768 1969-12-31 19:00 SEA_DISK_

SEA_DISK_ appears to contain all my folders and files, but SEA_DISK does not:

tim@bluemonster2:/$ ls /media/SEA_DISK_
18e1f2171828ff4f73            asus                  Recycled
28f1c8eddb730a13ed            bluemonster           System Volume Information
33862fcba5f9b712296359ae      compaq                test.txt
554246c0e264761b3d497e692dab  d1d0c9c1967b9b0e9cee  ubuntu
aa6d6d98a42253aaa6f7f7        gd                    windows

tim@bluemonster2:/$ ls /media/SEA_DISK
test.txt  ubuntu

Here's what fdisk -l has to say.  I don't understand this very well, but it seems to be frequently asked as part of troubleshooting.  My internal/boot HDD is /dev/sda; my external HDD is /dev/sdb

tim@bluemonster2:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb73cb73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6438    51713203+   7  HPFS/NTFS
/dev/sda2            6439       14593    65505037+   5  Extended
/dev/sda5            6439       14405    63994896   83  Linux
/dev/sda6           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00001482

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32
tim@bluemonster2:~$

In Nautilus, the left hand "places" menu displays SEA_DISK but when hovering over it and then clicking it you see right away that it's pointing to /media/SEA_DISK_

Would appreciate any suggestions for restoring SEA_DISK to its rightful place in my system, and whacking SEA_DISK_ , or at least the next steps in troubleshooting.  Thank you.

---

### Post by lmarmisa on 2010-05-07
Please, start your Ubuntu system without any external HDD connected and repeat the command:

> ls -l /media
Best regards,

Do you see any SEA_DISK* directory?

Best regards,

Luis

---

### Post by tt9024 on 2010-05-07
Shutdown, disconnect external HDD, restart, then ls -l /media.  SEA_DISK is still present.  This is the correct name but with incorrect files etc.  Not to mention that the corresponding HDD is completely disconnected.  Output pasted below.  What next?  Thanks, Luis.

tim@bluemonster2:~$ ls -l /media
total 16
lrwxrwxrwx 1 root root    6 2008-05-03 07:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-05-03 07:50 cdrom0
drwxr-xr-x 2 root root 4096 2008-05-03 07:50 cdrom1
lrwxrwxrwx 1 root root    7 2008-05-03 07:50 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2008-05-03 07:50 floppy0
drwx------ 3 tim  root 4096 2010-05-07 17:19 SEA_DISK
tim@bluemonster2:~$ ls -l /media/SEA_DISK
total 8
-rw-r--r-- 1 tim tim   13 2010-05-07 17:19 test.txt
drwxr-xr-x 3 tim tim 4096 2010-05-04 11:10 ubuntu

---

### Post by lmarmisa on 2010-05-07
I understand that you have no other partition named SEA_DISK.

If so and the files in the directory /media/SEA_DISK seem rubbish, try to delete or rename that directory with the external HDD disconnected.

You can be conservative and rename the directory typing:

> 
sudo mv /media/SEA_DISK /media/RUBBISH


Then, restart your system with the ext HDD connected and check if the problem is solved.

Luis

---

### Post by tt9024 on 2010-05-07
FIXED!  Thank you very much, Luis.  Muchas gracias.  Have a great weekend!  Tim

---

### Post by lmarmisa on 2010-05-07
Great!.

Don't forger to remove the RUBBISH directory. ;)

Hasta pronto,

Luis ):P

---


---
title: "USB Stick partition permissions"
date: 2006-06-01
forum: General Help
---

### Post by static chaser on 2006-06-01
I have a 1GB Memorex USB stick that I partitioned using GParted.  I left the FAT16 for files that I use at work.  We are still using Windoze 98 (yes 98) so I left them Fat16.  I created a large portion of the stick as ext2 for data storage, backup etc.  When I plug it in I get 2 drives on my Gnome desktop, one is Traveldrive, the other is 780MB  Removable Volume.  They also show up as /dev/sda1 and dev/sda2.  I can access the FAT16 ok from both Ubuntu and Windoze.  The problem is that I cant access the ext2 partition.  Under the permissions it says that root is the owner and I cant change anything because I am not the owner.  There are no files showing on the ext2.  Thanks for any help in advance.

---

### Post by aysiu on 2006-06-01
It shows up twice? That's weird.

Let's say the Ext3 partition shows up as /media/removable

```
sudo chown -R staticchaser:staticchaser /media/removable
```

---

### Post by static chaser on 2006-06-01
OK I tried that, still no joy.  Please bear with me on this command line usage.  I have not used command line since DOS 2.1 and am still learning.  It was about midnight here when I posted the original.  I have searched the forums and tried several different command line entries but chmod or chown do not work.  The USB stick was already formated for FAT 16 because I used it for work and XP file backup here at home.  I used GParted to resize the FAT16 and then installed a ext2 partition.  Should it be a ext3 partition?  When I look at the partition under properties it says 780 MB drive with 728.7 available and nothing on the drive.

---

### Post by aysiu on 2006-06-01
Can you post the output of these two commands (when you have the USB stick plugged in)? ```
sudo fdisk -l
df -h
```

---

### Post by static chaser on 2006-06-01
Here they are! Took me a few minutes.
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11926    95795563+  83  Linux
/dev/hda2           11927       12161     1887637+   5  Extended
/dev/hda5           11927       12161     1887606   82  Linux swap / Solaris

Disk /dev/sda: 1027 MB, 1027604480 bytes
16 heads, 32 sectors/track, 3920 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         800      204784    e  W95 FAT16 (LBA)
/dev/sda2             801        3920      798720   83  Linux
day@ubuntu:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              90G  1.9G   84G   3% /
tmpfs                 316M     0  316M   0% /dev/shm
tmpfs                 316M   13M  304M   4% /lib/modules/2.6.12-10-386/volatile
/dev/sda1             200M   60M  140M  30% /media/TRAVELDRIVE
/dev/sda2             768M   24K  729M   1% /media/usbdisk

---

### Post by aysiu on 2006-06-01
Okay. Can you post the output of these commands? Substitute your real username for *username*. ```
sudo chown -R *username:username* /media/usbdisk
sudo chmod -R 755 /media/usbdisk
cd /media/usbdisk
ls -a
```

---

### Post by static chaser on 2006-06-02
day@ubuntu:~$ sudo chown -R day:day /media/usbdisk
Password:
day@ubuntu:~$ sudo chmod -R 755 /media/usbdisk
day@ubuntu:~$ cd /media/usbdisk
day@ubuntu:/media/usbdisk$ ls -a
.  ..  .Trash-root
day@ubuntu:/media/usbdisk$

---

### Post by aysiu on 2006-06-02
It looks as if everything's good.

Can you try creating a file on that part of the USB stick?

---

### Post by static chaser on 2006-06-02
Yeah that worked! I can read write to the linux portion of the usb disk.  Thanks for all the help.                                          static chaser

---


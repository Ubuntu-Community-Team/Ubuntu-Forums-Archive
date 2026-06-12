---
title: "Old hard drive"
date: 2009-07-14
forum: General Help
---

### Post by cowboy7305 on 2009-07-14
I have just taken my old hard drive out of my old computer and it has a complete operating system of windows xp on it ,i have bought a usb shell to go over it to make it usb compatible ,when i load look at it via ubunto pn my desktop it comes up as a media storage device of round 118 gig ,is there any way i can read the data or retrieve data ,like pictures from this device ,or can it be used as an external op system ,i am using ubunto 9.04 full install 
many thanks 
ps i have no idea what iam doing ,if its not drag and click i am lost

---

### Post by earthpigg on 2009-07-14
when you open it in places -> computer, do you see all the stuff on it?

ie: places -> computer -> 118 GB Media -> My Documents -> -stuff-

---

### Post by cowboy7305 on 2009-07-14
/media/disk/bin
/media/disk/boot
/media/disk/cdrom
/media/disk/dev
/media/disk/etc
/media/disk/home
/media/disk/lib
/media/disk/lost+found
/media/disk/media
/media/disk/mnt
/media/disk/opt
/media/disk/proc
/media/disk/root
/media/disk/sbin
/media/disk/srv
/media/disk/sys
/media/disk/tmp
/media/disk/usr
/media/disk/var
/media/disk/initrd.img
/media/disk/vmlinuz


this is what i see on disk just in thunbnail though,nothing about windows

---

### Post by earthpigg on 2009-07-14
easy/lazy way to see what is mounted:

df -h

if you don't see something that looks familiar there, try this:

ls -R | grep Windows

and/or

ls -R | grep windows

and/or 

ls -R | grep WINDOWS


(i cant remember if windows is capitalised or not!)


you can replace 'windows' with any folder or file you know to exist on your windows partition.

---

### Post by tommcd on 2009-07-15
With the external drive plugged in, open a terminal and run:
```
sudo fdisk -l
```
This will list all your partitions, including the external drive.
To see if the partition(s) on the drive are mounted, just run the **mount** command. Post the output of the fdisk and mount commands here.
You should be able retrieve pictures and data on the drive.

---

### Post by TeamJ on 2009-07-15
I forget how this works, but try searching your whle computer for a file YOU KNOW is on it.

---

### Post by cowboy7305 on 2009-07-15
looks like i had already deleted disk 
this is what i get when i run sudo fdisk -l 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60046   482319463+  83  Linux
/dev/sda2           60047       60801     6064537+   5  Extended
/dev/sda5           60047       60801     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c1d1c1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
mine@mine:~$ 

when i look on desk top i sea the 120gig drive is there with one file in it called lost and found 
but i can not copy any thing to the disk tells me i The folder ======cannot be copied because you do not have permissions to create it in the destination.

---

### Post by tommcd on 2009-07-16
> **cowboy7305 said:**
> looks like i had already deleted disk 
this is what i get when i run sudo fdisk -l 
...
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c1d1c1d

Device Boot Start End Blocks Id System
/dev/sdb1 1 14593 117218241 83 Linux
mine@mine:~$ 

when i look on desk top i sea the 120gig drive is there with one file in it called lost and found 
but i can not copy any thing to the disk tells me i The folder ======cannot be copied because you do not have permissions to create it in the destination.
Your output from 'sudo fdisk -l' indicates that there are no NTFS (i.e., Windows XP) partitions on the old hard drive you have hooked up.
You must be right about already deleting the files on the drive.

---

### Post by TeamJ on 2009-07-16
make a new partition on your main HDD, boot off the old one and transfer files to the new partition, use linux to copy those files over and get rid of the partition, reformat the old HDD

---

### Post by ramnarayan on 2009-07-16
try testdisk 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---


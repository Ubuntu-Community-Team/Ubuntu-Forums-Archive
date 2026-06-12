---
title: "I'm trying to access my hard drive through Ubuntu usb, no permissions."
date: 2012-03-20
forum: General Help
---

### Post by Mynxenoa on 2012-03-20
I know I need to change the permissions but I do not have much knowledge of the command line. When I attempt to change the permissions just by clicking around on the permissions tab it will automatically force it back to create and delete files and it will not allow me to even access the files. What can I do to make a solid attempt and get to these files on the harddrive? The hard drive has Windows Vista OS on it and I'm not sure if its conflicting or security related. I would like to understand as well as get to the files. Thank you for reading.

---

### Post by sudodus on 2012-03-20
What file system is it that you want to access via Ubuntu? If it is a Windows system (FAT or NTFS), the permissions are set when the partition is mounted, and they cannot be changed. Please post the output of the following commands
```
sudo fdisk -lu
```
and
```
cat /etc/mtab
```

---

### Post by gordintoronto on 2012-03-20
I don't understand this at all. 

I download an Ubuntu ISO, for example Precise Ubuntu 12.04 64-bit (beta), and use Unetbootin to create a bootable flash drive. I boot from the flash drive, and I start the file manager, and I have complete control over every file on my laptop, which has Windows 7 and several Linux partitions. On the left side of the window, I click on "169 GB File system," and there are the Windows 7 files. Similarly for the other partitions on the drive.

I have no issue with permissions, don't need to use the command line, everything "just works."

---

### Post by gleedadswell on 2012-03-20
I'm surprised you can't access the files just by opening a file manager and clicking on "**** GB Filesystem".

If you're booting from the live cd .iso on a usb then here's a way that should work.

Open Disk Utility (i.e. by using the Dash).

In the list of devices on the left click on the hard disk, then in the list of volumes in the main part of the window click on the windows partition that you are trying to access (it is probably indicated as "*** GB NTFS").  Down below that click the "Mount Volume" button that should be available.

Now you should be able to access the files in several ways.  It should be available as "*** GB Filesystem" if you open the file manager.  Or, note in Disk utility where the volume is mounted; it will say something like:

Mount point: Mounted at /media/********

So in a terminal just navigate to that part of your filesystem:

cd /media/******

where ***** is the random seeming string of characters that Disk Utility told you.  This should put you at the root of the windows directory tree.

---

### Post by MasterGamerJK on 2012-03-21
Unless you have your windows permission encrypted in some form?

---

### Post by Mark Phelps on 2012-03-21
Reads like you're trying to change permissions on file in the Vista partition, right?  So, why are you trying to do that?  IF you only need to copy off the files, you don't need to change permissions to do that.

---


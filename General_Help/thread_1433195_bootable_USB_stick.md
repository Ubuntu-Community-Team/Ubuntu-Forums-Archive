---
title: "bootable USB stick"
date: 2010-03-18
forum: General Help
---

### Post by RutRow on 2010-03-18
I am a noob at Ubuntu. I currently have 8.04 and I am looking at upgrading to 8.10 and beyond. I want to make a recovery disk with Clonezilla so if something goes wrong with the upgrade I can go right back to where I am now. I have a 16 Gig thumb drive that I want to boot Clonezilla from. Then I want to burn an image to my DVD burner.  
 

 I am stuck at one point in the process. I am reading the instructions from
  [http://clonezilla.org/clonezilla-live/liveusb.php](http://clonezilla.org/clonezilla-live/liveusb.php)
 

 This part is where I am stuck is step 4.
 To make your USB flash drive bootable, first change the working dir, e.g. "cd /media/usb/utils/linux", then run "bash makeboot.sh /dev/sdb1" (replace /dev/sdb1 as your USB flash drive device name), and follow the prompts to finish that.
 

 My USB drive is named M-S325 so if I enter cd/ media/M-S325/utils/linux in terminal I get the error no such file or directory. I know it is something stupid simple I am doing wrong, but I am stuck.  
 

 What do I need to do to make my UBD drive bootable with Clonezilla ?

---

### Post by spiderbatdad on 2010-03-18
as you cd into /media/... use ```
ls -al
``` to see the actual directory names.
Also unetbootin has a version of clonezilla and is very user friendly.

---

### Post by RutRow on 2010-03-18
> **spiderbatdad said:**
> as you cd into /media/... use ```
ls -al
``` to see the actual directory names.
Also unetbootin has a version of clonezilla and is very user friendly.

I will check unetbootin. Thanks

I still want to know what I am doing wrong in that step 4.

---

### Post by spiderbatdad on 2010-03-18
if it says file does not exist then you have the file name wrong, hence the suggestion to use ls to lead you to the correct filename. For example:
```
 cd /media
ls -al
cd <next directory>
ls -al 
```
and so on.

---

### Post by ajgreeny on 2010-03-18
The bit in brackets, "(replace /dev/sdb1 as your USB flash drive device name)", means the /dev/sdx# name, not the make or model of the flash disk.  Attach the flash disk and run sudo fdisk -l in terminal; that will tell you the name of the drive/partition, which you will be sure is right because of the reported size.

---

### Post by RutRow on 2010-03-18
I guess I am dense. I don't understand where the ls - al would be used.

---

### Post by spiderbatdad on 2010-03-18
ok you're in the terminal and you cd /media then you ls and you see M-S325 listed. Then you cd M-S235, and you run ls again. Then you cd usb or utils (whatever it is) and you ls again, and so forth until you find the directory of file where your chain is failing.

---

### Post by RutRow on 2010-03-18
OK, I open terminal and type cd /media and I get:

glen@glen:/media$ ls -al
total 20
drwxr-xr-x  3 root root 4096 2010-03-18 17:02 .
drwxr-xr-x 21 root root 4096 2010-03-16 20:57 ..
-rw-r--r--  1 root root  112 2010-03-18 17:02 .hal-mtab
-rw-------  1 root root    0 2010-03-18 17:02 .hal-mtab-lock
drwx------  9 glen root 8192 1969-12-31 18:00 M-S325
glen@glen:/media$ 


If I type cd M-S325 I get the same - No such file or directory

Thanks for the help. This has to be simple and the lightbulb will go off over my head any minute.

---

### Post by RutRow on 2010-03-18
I am getting closer!

I got to the folder and ran the  bash makeboot.sh /dev/sdb1
and got this error. 

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders
Units = cylinders of 3000 * 512 = 1536000 bytes
Disk identifier: 0xd883b4cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10443    15663084    c  W95 FAT32 (LBA)
--------------------------------------------
Are you sure you want to continue?
[y/n] y
OK! Let's do it!
--------------------------------------------
makeboot.sh: line 147: parted: command not found
/dev/sdb1: this doesn't look like a valid FAT filesystem
Program terminated!

So do I have to format the drive? Close but yet so far.

---

### Post by spiderbatdad on 2010-03-18
right it sounds like your drive is not formatted.
fdisk on the flash drive will do this. Always be careful using fdisk. getting the device wrong can be ruinous!
See some tutorials like this:[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

And there are many example on using fdisk to format and make flash drives bootable if you really want to go commando style.

mmm. might also be caused by ext4 filesystem not recognized. Sorry I don't know more.

---

### Post by RutRow on 2010-03-19
> **spiderbatdad said:**
> right it sounds like your drive is not formatted.
fdisk on the flash drive will do this. Always be careful using fdisk. getting the device wrong can be ruinous!
See some tutorials like this:[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

And there are many example on using fdisk to format and make flash drives bootable if you really want to go commando style.

mmm. might also be caused by ext4 filesystem not recognized. Sorry I don't know more.


Thank YOU!!!! :p:p :popcorn:

UNetbooting rocks. It made my drive bootable and CloneZilla lives!. Now I need to figure out Clonezilla and make my clone backups.

---


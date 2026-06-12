---
title: "Access to Windows partitions under Linux"
date: 2006-03-13
forum: General Help
---

### Post by ickmaul on 2006-03-13
Hello of people I is an absolute Linux beginner.  On my Home PC beside Windows XP Prof / Ubuntu installed.  Are mega contently with the operating system.  However wanted I mean Mp3s of my Windows partition under Linux to get.  There I get then the message that I the necessary rights of access do not have.  Sadly have already diverese things tried out like etc/fstab to change the this failed however everything (it could changes brought however nothing).  White genuinly not which I to still make is...  The whole already with sudo chmod 777 etc.... tried.  Everything did not function.  After I chmod 777 did not implement came the message one while no more that I no access do not have however the data have I nevertheless seen.  What still make can I the file system for under that my Mp3s drauf are is ntfs. white somebody which?  Are an absolute beginner in the area however perhaps gibts someone that me that to really explain can thereby also I it as (still) Linux noob understand signs P.s.  As "roots" in the console seh I the files thus data already are drauf!  Haett nevertheless I gladly as a "normal user" access drauf Smilie thanks already times for your answers.  Love of greetings ickmaul 

P.s. My Englisch is very bad but i hope you can read this post ;)

---

### Post by mlind on 2006-03-13
If I gathered right, you want to mount windows (fat/ntfs) partition on your linux box?

check this article which describes it [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

at first, you need to find out the device handlers of your partitions, you can do this
by opening terminal from Applications > Accessories > Terminal

to terminal, type command 
```
sudo fdisk -l
```

you should get list of all your partitions. Look for lines that have System
attribute of NTFS or FAT. Like this one:

```

Device Boot      Start         End      Blocks   Id  System
/dev/hda5               2       12724   102197466    7  HPFS/NTFS

```

These are windows' partitions. After you've identified them, follow the MountingWindowsPartitions tutorial.

I've got the partitions displayed before on /*etc/fstab* as
```

/dev/hda5       /media/E        ntfs    ro,auto,nls=utf8,umask=0222     0       0

```

where 
*ro* is for read-only
*auto* makes drive mount automatically
*umask=0222* definition allows all users to access the drive's contents

---

### Post by TLE on 2006-03-13
Try pressing the help-button, (that's the life-preserver thingy in the top panel). Press Ubuntu 5.10 Starter Guide. A table of contents will appear and number 5 on it should be Windows partitions. Plus I thought I saw a couple of German words in your post, since German is a relatively big langauge it might be translated, making things a bit easier for you

---


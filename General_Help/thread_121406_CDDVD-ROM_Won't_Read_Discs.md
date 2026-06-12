---
title: "CD/DVD-ROM Won't Read Discs"
date: 2006-01-25
forum: General Help
---

### Post by blue_thunder on 2006-01-25
After watching a movie last night, I shut down the computer. I woke up this morning and noticed that on the desktop was no longer "The Matrix" mounted DVD, but simply "CD-ROM," as if it were a blank disc. I took it out, put it back in...tried it with a few others. The blank CD-ROM image went away after the third DVD, nothing seems to be mounted, but now it won't read any DVDs.

Any help you can give would be appreciated,

Shaun

---

### Post by Who on 2006-01-25
Hi,

Someone else may be able to solve this without, but could you please post your /etc/fstab for us to look at (in Gnome or KDE hit alt+F2 or open a terminal and type 'gedit /etc/fstab' without the quotes). 

Another place to look for evidence would be the System-->Administration-->Disks dialogue.

To see if the problem is that it isn't mounting automatically open up the Disks dialogue and try set up an 'Access Path' (actually a 'mount point') for the CDRom drive - then click the 'Enable' button - see what happens. This is just another way of mounting a disk - you could do it at the command line using 'mount /dev/[the device of your CDRom drive - like hdb1 or hdc etc...) /media/[cdrom or dvd or wherever you want to put it...you could put it in /home/you/monkey if you like....]' if the drive IS in fstab ('file system table') otherwise, you need to specify some options best found by typing man mount at a terminal

I have a problem at the moment with a USB hard disk that has stopped automounting - which could be very similar to your problem here - so if you do do solve it please post how you did.

Good luck

Who

---

### Post by blue_thunder on 2006-01-25
When I tried to mount the disc using "mount /dev/hdc" I got the following:

```
$ sudo mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


When I entered "gedit /etc/fstab" I got:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by dcstar on 2006-01-25
[QUOTE=blue_thunder]When I tried to mount the disc using "mount /dev/hdc" I got the following:

```
$ sudo mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


When I entered "gedit /etc/fstab" I got:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```[/QUOTE]
My fstab has the following:

/dev/hdd        /media/cdrom0   udf,iso9660	ro,user,noauto,noatime			0       0

---


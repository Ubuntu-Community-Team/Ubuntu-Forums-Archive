---
title: "problems transferring files to USB hard drive"
date: 2009-07-03
forum: General Help
---

### Post by upa_bigtree on 2009-07-03
Hi, please can anyone help!

i'm having problems copying files from my laptop to my USB hard drive. 

when i try to copy a file, it will begin to transfer quickly at first but then slows or stops, after a minute or two a warning box appears saying

[B]"Error writing to file: Input/output error"
[/B]
i have managed to copy pictures with no problems, but always get this message when copying music or video, so i presume its either multimedia or larger files???

i have recently done a fresh install of Jaunty 9.04, after previously using Hardy which did not give me this problem. (How is it possible to go backwards whilst trying to go forwards...)

anyway all help will be appreciated, thanx:guitar:

---

### Post by ajgreeny on 2009-07-03
Are the video files larger than 4GB and is the usb drive formatted to fat32?  If so, that is the problem.  Format it to ntfs (or even ext3 if for linux use only) and try again.

---

### Post by philcamlin on 2009-07-03
what format is the usb

---

### Post by upa_bigtree on 2009-07-03
sorry but i'm abit of a noob, how can i find out the format of my usb?

also i have tried many different files, all different sizes...

---

### Post by upa_bigtree on 2009-07-03
Thanx for your replies but i'm still unsure on how to check what format my USB is? or how to change it, if that is the problem!

---

### Post by blueridgedog on 2009-07-03
> **upa_bigtree said:**
> sorry but i'm abit of a noob, how can i find out the format of my usb?



You can run (and post the output of)
```

sudo fdisk -l
```

While the drive is plugged in.

The output of 

```
mount
```

would help as well.

---

### Post by Hobgoblin on 2009-07-03
> **upa_bigtree said:**
> Thanx for your replies but i'm still unsure on how to check what format my USB is?

In that case it is almost certainly FAT32

>  or how to change it, if that is the problem!

Pretty irrelevant if the files are not over 4GB, but I would install gnome partition editor from add/remove and use that.  There is also Gnome Format which may be easier to use.

---

### Post by upa_bigtree on 2009-07-04
> **blueridgedog said:**
> You can run (and post the output of)
```

sudo fdisk -l
```

While the drive is plugged in.

thanx blueridgedog, 

i typed the command into the terminal and got the following:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x167542cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)


so it would seem it is FAT32, my next question is:
```
mount
```
what exactly will this do, will this affect me being able to use my hard drive on other computers and my ps3?

---

### Post by alphacrucis2 on 2009-07-04
> **upa_bigtree said:**
>  my next question is:
```
mount
```
what exactly will this do, will this affect me being able to use my hard drive on other computers and my ps3?

mount without any arguments is informational. It just tells you information about each current mount.

---

### Post by upa_bigtree on 2009-07-04
thanx, i'm such a noob, or still recovering from last weeks glastonbury festival...
"mount" gave me

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sdb1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

any ideas on how i can fix this problem? i have installed gnome partition editor and gnome format from add/remove, but am not sure what to do with them.

---

### Post by blueridgedog on 2009-07-04
> **upa_bigtree said:**
> 
/dev/sdb1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


This is your external drive, and it is formated "vfat" for fat32, which means it has a 4 gig limit to the size of files.  Are any of the files you are trying to copy over 4 gig?  If so that is the cause of your error.  

I can talk you through formating it with another file system that can handle larger files.  Do you share this drive with other computers or operating systems?

---

### Post by upa_bigtree on 2009-07-04
> **blueridgedog said:**
> This is your external drive, and it is formated "vfat" for fat32, which means it has a 4 gig limit to the size of files.  Are any of the files you are trying to copy over 4 gig?  If so that is the cause of your error.  

I can talk you through formating it with another file system that can handle larger files.  Do you share this drive with other computers or operating systems?

i have this problem with files smaller then 4 gig, some are only about 1 gig. but when i was using Hardy i could copy all files of any size, some over 10 gig.

i share this drive with my playstation 3, and sometimes friends pc's,

your help is very much appreciated, and a walk through would be great, thanx...

---

### Post by blueridgedog on 2009-07-04
Given how you share the drive, vfat/fat32 is the best choice.  Do you dual boot?  If so I suggest running check disk in windows to check the disk for errors.  I would also suggest trying a different USB cable or a different USB port.

---

### Post by upa_bigtree on 2009-07-05
Once again, thanx alot for all your help and time. Unfortunately i don't duel boot, i decided a long time ago that i hate windows, so went balls deep into linux... so i will have to run check disc on a friends pc later.

also i have tried different usb cables and ports.

---

### Post by blueridgedog on 2009-07-05
You can check it from your Linux system:

Unmount it first:

```
sudo umount /dev/sdb1
```

then

```
sudo fsck.vfat /dev/sdb1
```

---

### Post by upa_bigtree on 2009-07-06
cool, it appears were gettin closer to fixing this... i typed the code in and got the following:

dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset: original/backup)
  65:01/00, 67:bd/47, 68:02/3e, 69:1a/09, 70:4b/14
1) Copy original to backup
2) Copy backup to original
3) No action

i chose 3) no action, and got the following:

FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT

at this point i got scared and bailed out, just incase i got it wrong and lost over 200 gig of files.

---

### Post by blueridgedog on 2009-07-06
> **upa_bigtree said:**
> 
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT

at this point i got scared and bailed out, just incase i got it wrong and lost over 200 gig of files.

Do you have the ability to make a backup of the files before proceeding?  I strongly recommend that you have a working backup before ding file system maintenance.

Most users select number 1, after which you will go through a long process of file by file questions.

It may have been that the disk was disconnected without being unmounted (right click the icon and select eject or unmount).

---

### Post by upa_bigtree on 2009-07-06
unfortunately the drive causing all the problems is my back up, and i always unmount it properly. 

i might be able to borrow a friends drive to back it up, and then a full format will be possible. but if there is a corrupt file, will copying this affect my friends drive?

---

### Post by blueridgedog on 2009-07-06
It should not affect the other drive and it is a good plan to back it up and then format it.  The unclean unmounted may have happened when connecting to the game console or at some other point (or never as there is no guarantee what is causing the issues).

---

### Post by upa_bigtree on 2009-08-08
firstly many thanx to blueridgedog, and appologies for the long delay in my reply. i'm still having the same problem but have narrowed down the problem...

the problem is not with my external drive but my laptop (or jaunty) as i can copy files perfectly on my friends computer which is also running on jaunty.

also, gtkpod crashes when copying music over to my i-pod.

both of these problems are obviously connected, and hopefully the new information might help solve the problem.

---


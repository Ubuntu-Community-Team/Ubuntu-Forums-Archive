---
title: "Resizing or merging partitions"
date: 2012-01-22
forum: General Help
---

### Post by asvestomix on 2012-01-22
Hello there

First of all i would like to describe how my partitions looks like right now:

1) this computer runs a dual boot with windows, 
2) Ubuntu are installed on a partition of 25GB
3) this 25gb partition is separated into 4 logical partitions
4) 500 mb for /boot
5) 1GB for Swap
6) 7gb for /
7) 19GB for /home

So it seems that i calculated the partition sizes wrong and right now i am running out of space at / and my /home is almost empty (since i use an ntfs partition for my files so they can be accessed by windows)

What i would like to do now and i don't know how is to merge the "/" with "/home".

---

### Post by lechien73 on 2012-01-22
I would suggest that you download the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php").

Create the CD and boot from it, you can then dynamically re-size your partitions.

Be advised that it's a good idea to make a full backup before doing anything with your partitioning structure, and you're probably best just shrinking /home rather than removing it altogether.

---

### Post by davethewave83 on 2012-01-22
> **asvestomix said:**
> Hello there

First of all i would like to describe how my partitions looks like right now:

1) this computer runs a dual boot with windows, 
2) Ubuntu are installed on a partition of 25GB
3) this 25gb partition is separated into 4 logical partitions
4) 500 mb for /boot
5) 1GB for Swap
6) 7gb for /
7) 19GB for /home

So it seems that i calculated the partition sizes wrong and right now i am running out of space at / and my /home is almost empty (since i use an ntfs partition for my files so they can be accessed by windows)

What i would like to do now and i don't know how is to merge the "/" with "/home".

any way you go you will need to back-up your files

easiest way to do this: backup your files and then "destroy";
by destroy I mean start all over from fresh install

harder way: backup your home and then boot a liveCD,(or better, backup the home from liveCD) from LiveCD using gparted delete /home partition, then resize / to be larger 

but this will create problems as the files of / tell it that home is on the partition you just deleted, so you'd have to re-configure the files which point to /home on that partition (/etc/fstab) 

so gedit the /etc/fstab and carefully remove the mount for /home

create a new directory in / called home

restore your backedup files to /home 

/ will then be merged with /home

it will not however be NTFS unless / is NTFS which is highly unlikely. ;)

I almost forgot
if you go the harder way, when you restore your files to /home from the backup you will need to change ownership of your user folder to you (otherwise it will be owned by root) 

so from a livecd terminal window use chown -R user:user /home/user

where "user" is the name of your user folder and /home/user is the path
(if the drive is mounted /media/sda3/ then it will be /media/sda3/home/user from the livecd)

---


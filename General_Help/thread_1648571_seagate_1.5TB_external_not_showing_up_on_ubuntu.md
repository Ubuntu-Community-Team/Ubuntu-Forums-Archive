---
title: "seagate 1.5TB external not showing up on ubuntu?"
date: 2010-12-19
forum: General Help
---

### Post by ibootindos on 2010-12-19
I'm running ubuntu 10.10 netbook remix from my hp mini. I have a seagate 1.5TB that works just fine on windows, but when I plug in the usb cord in ubuntu there's no reaction whatsoever, how do I fix this?

---

### Post by Meow27 on 2010-12-19
two questions
1) does the enclosure you are using support drives of 1.5 TB+? (edit: reread your post. it works with windows so this was a bad/stupid question)

2) run this and give us the output please
```
sudo fdisk -l
```
this will list all the drives (partitions) seen by your machine.

---

### Post by ibootindos on 2010-12-19
root@ubuntu:/etc# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1bfc1bfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156279296    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaebb1f2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

---

### Post by ibootindos on 2010-12-19
I'm pretty sure its at /dev/sdb but when I try to mount it I get an error about /etc/fstab or something. lol

---

### Post by Meow27 on 2010-12-19
alright here is a temporary fix to the problem. I can make a script for you if you want, but this should work for you

for sake of orginization, lets make a seperate folder in your /media area

```
sudo mkdir /media/harddisk0
```
this will create a folder "harddisk0"

seems your whole harddisk is formatted in NTFS
```
 sudo mount -t ntfs /dev/sdb1 /media/harddisk0
```
this will force mount the external drive to /media/harddisk0

[COLOR="Yellow"]now I dont know how to do a proper unmount, but from experience doing a [cod] sudo umount -t ntfs /dev/sdb /media/harddisk0[/code] (notice its umount) does the trick albeit very dirty[/COLOR]
edit: to unmount either do a ```
sudo umount /dev/sdb1 
``` 

but its MUCH safer to do a ```
sudo umount /media/harddisk0
```

---

### Post by ibootindos on 2010-12-19
> **Meow27 said:**
> alright here is a temporary fix to the problem. I can make a script for you if you want, but this should work for you

for sake of orginization, lets make a seperate folder in your /media area

```
sudo mkdir /media/harddisk0
```
this will create a folder "harddisk0"

seems your whole harddisk is formatted in NTFS
```
 sudo mount -t ntfs /dev/sdb /media/harddisk0
```
this will force mount the external drive to /media/harddisk0

now I dont know how to do a proper unmount, but from experience doing a ```
 sudo umount -t ntfs /dev/sdb /media/harddisk0
``` (notice its umount) does the trick albeit very dirty



so here's the error message I got..

joshua@ubuntu:~$ sudo mount -t ntfs /dev/sdb /media/harddisk0
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by Meow27 on 2010-12-19
sorry. I made many mistakes in my previous post. Its edited they way it should be. the yellow text is what i had, i messed it up and colored it so you know i edited it and that its just wrong.
edit: yes I should have wrote sdb1 instead of sdb. I got sloppy.

---

### Post by ibootindos on 2010-12-19
> **Meow27 said:**
> sorry. I made many mistakes in my previous post. Its edited they way it should be. the yellow text is what i had, i messed it up and colored it so you know i edited it and that its just wrong.


so I ran the ***mands, and its mounted, but I can't see it on the desktop and this new 10.10 confuses me, I don't know how to navigate at all. :/

---

### Post by Meow27 on 2010-12-19
ok open up your home folder
get to the root folder (/) ((your home folder is /home/username))

there you will see a bunch of folders. look for /media
when you are there, look for harddisk0

now click on harddisk0, ctrl+shift and drag the folder to your desktop. this should create a short cut. now try accessing the folder.

hope it works :)

EDIT: you can do a ```
nautilus /media/harddisk0
``` in the terminal too.

---

### Post by ibootindos on 2010-12-19
thanks!

---

### Post by Meow27 on 2010-12-19
Since this mount will no longer exist after a restart/shutdown, here are scripts you can place anywhere to click on as executables.

if you want to know the contents, you can look inside, but ill give em to you just in case
```
gksudo mount -t ntfs /dev/sdb1 /media/harddisk0
gksudo umount /media/harddisk0
```
gksudo is sudo but with a gui. this will ask you for your password in a window instead of a terminal.

im not sure how sh's are treated system to system. so just incase if it doesn't run, click on the file properties, then click on the permissions tab, if the "run as executable" area is unchecked, check it. do this for both files 
(remember this is if the file doesn't execute when you double-click, but rather opens up as a text)

have fun with ubuntu :popcorn:

---


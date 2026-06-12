---
title: "Cannot Transfer files from CD/DVD to HDD"
date: 2009-10-11
forum: General Help
---

### Post by jngrim on 2009-10-11
Can someone tell me why I cannot copy mp3 files from CD/DVD to my HDD either in the command line using sudo cp nor in nautilus?

IN the CL

sudo cp * /home/usr/music/
error: omitting Directory

if I use gnome and drag and drop, I get an input/output erro and cant copy over any files. 

Any help would be great.

---

### Post by delcypher on 2009-10-11
Sounds like dodgy drive / Disc but you can try a few things.

Can your drive mount and read other discs okay or is just this disc?

You could try using dd command to make a copy of the disc then try and mount it. Here's the code to do that (assuming your drive is /dev/sr0, if you want to find out what it's name is when the CD is mounted run mount and look for the device corresponding to the mount pointed you know belongs to the CD)

```

sudo umount /dev/sr0 #makes sure drive is unmounted
dd if=/dev/sr0 of=/home/username/mydisc.iso #Does disc dump to file
mkdir /home/username/temp_mount #create mount point to use
sudo mount -o loop -t iso9660 /home/username/mydisc.iso /home/username/temp_mount #tries to mount your disc image in temp_mount directory

```

If dd fails /dev/sr0 is still mounted or your drive can't read the disc properly (because the drive doesn't work very well or the disc is damanged).

You could try using a tool called dd-rescue (dd_rescue on the command line) instead of dd (note it's syntax is slightly different) but not sure how well that'll work.

This is the only thing I can think of seeing as you tried copying using sudo and that gave "input/output erro "

---

### Post by SuperSonic4 on 2009-10-11
sudo cp -R /media/disk ~

---


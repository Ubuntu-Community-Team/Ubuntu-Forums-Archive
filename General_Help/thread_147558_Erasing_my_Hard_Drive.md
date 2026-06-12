---
title: "Erasing my Hard Drive"
date: 2006-03-20
forum: General Help
---

### Post by sholdens12 on 2006-03-20
Can someone help me with a resource for zeroing out my hard drive, wiping everything off it, and starting over with a fresh install of Breezy? 

My computer's partitions got all messed up because I tried to install a bunch of new repositories (or maybe it was the new kernel I installed). Either way, I have no operating system on my Thinkpad. I can boot up via LiveCD, and I can get to a Unix prompt. 

I really want to start over. Please help. I'm a newbie, and need you to hold my hand.

---

### Post by ssam on 2006-03-20
you can run gparted from the live cd. i think you find it in system -> administration. gparted will let you delete and create partitions.

if you want to make sure the old data can never be recovered then you can zero the disk or overwrite it with random data. this can be done with the dd command.

first work out which disk you want to wipe. dont do this to a disk/partition with any useful information on it, you wont be able to get the data back.

ide disks a labled
/dev/hda  = first (primary master) ide disk (normally you main hard drive)
/dev/hdb  = second (primary slave)
/dev/hdc = third (secondary master) often cd drive
etc

partitons are
/dev/hda1  = first partitons on hda
/dev/hdb2   = second partitons on hdb
etc

to zero a disk run
```
sudo dd if=/dev/zero of=/dev/hdxx
```
replacing /dev/hdxx with the drive or partitons you want to wipe.

to overwrite with random data do
```
sudo dd if=/dev/urandom of=/dev/hdxx
```

---

### Post by Ramses de Norre on 2006-03-20
If you're sure you want to delete everything you can just pop in the installation disk, you can then choose to repartition and use the whole hard disk when you're at the partition part.
If you just want do delete everything without installing a OS on it: use gparted from the live cd, delete all existing partitions and create new ones in the unallocated space. The options are pretty clear then, and I assume you'll use the first method.
You can ask for more info though;)
PS: If you want win too: install that first!

---

### Post by sholdens12 on 2006-03-20
The problem was that I wasn't able to do a regular install because it wasn't giving me a chance to repartition the disk. 

I did the dd function, but I wasn't able to get to the last disk. When I get to the "Partition disks" screen, the overview of my partitions shows me nothing. Guided partitioning gives me nothing but the option to once again manually edit the partition tables. 

What am I doing wrong?

---

### Post by Ramses de Norre on 2006-03-20
Can you delete the partitions with gparted on live disc?
What's the error on dd?

---

### Post by ArizonaKid on 2006-03-20
I really like the utlility Active at Kill Disk.

[Click for the link]("http://www.killdisk.com/downloadfree.htm")

I have used this numerous times, and the basic version is free.  I usually download the iso and make the bootable disc.  The basic version will do a one time zero out, which I find is more than enough.  The paid version is I guess for Super Secret Gov't stuff. :) 

Coming from the Mac platform, this was something I always did prior to a new OS install.  OS X had a very good disk utility for this from the install CD.

---

### Post by Hexidigital on 2006-03-20
If you have an old Win98 boot floppy, insert that, and boot from the a: drive

Then type fdisk [enter]
then delete the existing partitions
DO NOT create any partitions... let the Linux Installer do that for you

Also, if that dosen't work, try booting from the floppy again
then type C:/format c:/s [enter]

then do the fdisk thingy in the beginning

good luck

-Hex

---

### Post by ArizonaKid on 2006-03-20
To add, if you need a good iso burner, I love DeepBurner.

[Click for Link]("http://www.deepburner.com/?r=download")

This is another tool in which the free version works really well.

---


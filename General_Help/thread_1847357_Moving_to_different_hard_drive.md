---
title: "Moving to different hard drive"
date: 2011-09-20
forum: General Help
---

### Post by rdbowers on 2011-09-20
I have some kind of a newbie-like questions, although I've been using Ubuntu for a few years now (and have been programming (simple) off and on and using computers since the mid 70s).  I know similar questions have been asked, but none seem to match what I want to do, although I read several different threads.

I need to move my current 10.04LTS install to a different drive and be able to run from that drive.  I don't want to start fresh because I have a ton of needed software installed on the system and it would take days to re-install everything.

Background:

I'm running 10.04LTS on a desktop, with multiple hard drives.  The setup is a bit crazy, but it's due to different needs at different times over the years.

I started out with a (fast SATA) 80gb hard drive and an older (IDE) 120gb (5 years ago), with the 80gb partitioned out to having a 55gb partition for Ubuntu and the remainder for Windows XP (for needed XP-only software).  The second drive was partitioned out with a data drive and a partition for Fedora (which I now no longer use).

I've since then added two 320gb drives... one purchased a year ago, and a used one I installed over the weekend.  These contain data and videos I've captured (the one purchased a year ago was copied over to the used one for use as the new data/video drive).

What I want to do is to move the Ubuntu install I have on the 60 gb partition onto the 320 I purchased a year ago, then repartition and reformat the 80gb and use that for other things (possibly as a software backup drive).  I will use the 120 gb strictly for data, although I plan to eliminate the Fedora partition from that one as well.  (The second 320 will have backups of some of the data, plus all of the videos.)

I'd run out of space on the "software" Ubuntu partition.  I have a lot of heavy science stuff I run, along with a virtual machine and Wine.  I need much more space I have now because I find that I may need to add a Windows 98 partition for a very specialized program (that only runs in 98) and some other stuff.

Questions:  What would be the easiest way to get the OS over to the 320gb drive and have it work?   Any needed changes to Grub... especially since I'm eliminating the Fedora partition as well?    Can I use GParted to add the Fedora partition to the 120Gb data partition without having to copy everything over and back (many Gb of data) first?   (I do plan on backing it up onto one of the other drives).

Also, any suggestions on a way to have the computer print out a list of installed software?  Not all of it comes from the Ubuntu repositories... like I said, I do run a lot of "strange" stuff.  That way (until I can get a backup drive that is big enough), I can more easily re-build my setup if something bad happens.

Thanks!

Bob

---

### Post by seawolf167 on 2011-09-20
Do a disk-to-disk clone using [Clonezilla]("http://www.clonezilla.org") (assuming you are going to a drive of equal or greater size). Boot off a Linux live cd once you get it imaged over (Grub and everything will transfer), and delete/resize/manage you partitions as you want. Boot into Ubuntu, run

```
sudo update-grub
```

and ensure that all your mount points are the same (if you make drive changes) in /etc/fstab

```
gksu /etc/fstab
```

as from 

```
sudo fdisk -l
```

---

### Post by spiky001 on 2011-09-20
Try ```
sudo dpkg --get-selections
```to get list of installed programs or ```
sudo dpkg --get-selections > programs.txt
```to get a text file

---


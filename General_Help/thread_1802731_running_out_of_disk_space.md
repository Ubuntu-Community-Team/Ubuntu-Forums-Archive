---
title: "running out of disk space"
date: 2011-07-12
forum: General Help
---

### Post by kedaar on 2011-07-12
Hi,

I am getting a message that I am running of disk space using ubuntu 11.04.  It is a new installation and while performing the install I chose a partition size of 20 gb for ubuntu, 300 gb for windows 7.

However in the disk usage analyzer, it shows only 4.7 gb total disk space of which 4.3 gb is used.

This is the result when I run "fdisk -l"
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             154       36630   292996769+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           37639       38914    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           36630       37639     8102913    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           36630       37260     5062656   83  Linux
/dev/sda6           37260       37639     3039232   82  Linux swap / Solaris

I am not certain what happend to the other 15gb?  

Appreciate any help that you can offer.

Thanks

---

### Post by WorMzy on 2011-07-12
Post the output of
```
df -h
```
and
```
sudo du -hxd 1 / | sort -h
```

---

### Post by drs305 on 2011-07-12
The most common problems are undeleted trash residing in the trash bins (your's and root's), large log files, and backups made to the / partition instead of another partition which didn't get mounted before the backup began.

I wrote a guide a while back about analyzing disk space problems which may give you some help.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by kedaar on 2011-07-12
Hi Wormzy, DRS,

Thanks for the reply.

The du command did not work for some reason, however the df command has shown the problem:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.8G  4.4G  140M  97% /
none                 1.5G  696K  1.5G   1% /dev
none                                  1.5G  3.8M  1.5G   1% /dev/shm
none                                  1.5G  124K  1.5G   1% /var/run
none                                  1.5G     0  1.5G   0% /var/lock

Perhaps I set the Ubuntu partition to only 10 gb.

/dev and /var have all of my free space, do you have any ideas on how to resolve this?

Thanks

---

### Post by WorMzy on 2011-07-12
Give the du command time to execute. It may take a while, depending on the number of files you have, as well as your processor's capabilities.

The df command shows that you are definitely low on disk space, and that's not too surprising considering you've only set aside 4.8G for / and you don't have a separate /home or data partition. GNOME+Unity will take up ~3GB from the get go, and that will only leave you with ~2GB of space for any additional applications, their config files, any personal files + downloads, etc.

Depending on where your space is being used (the du command will tell you), you should either: A) create a separate /home partition (or data partition if you want to share with Windows) with sufficient space for all your personal files, or B) increase the size of /, so that you have enough space to install more applications (and/or store more personal files).

---

### Post by drs305 on 2011-07-12
Actually, it looks like your Ubuntu installation is less than 6GB. If you have additional disk space, you could expand your Ubuntu partition. If you have Windows in a primary on sda1 and/or sda2 and Ubuntu in an extended partition on sda5, it may be faster and safer to resize and reinstall than trying to shrink and move partitions around. 

If you need help, here is a guide about resizing a / partition:
[Expanding /]("http://ubuntuforums.org/showthread.php?t=1219270")

If you have questions, a screenshot of sda from within Gparted would be helpful.

---

### Post by kedaar on 2011-07-13
Ok, I guess I should resize and reinstall, is there any instructions for doing this?

Thanks guys!

---

### Post by WorMzy on 2011-07-13
Reinstalling isn't necessary. You can just use gparted to resize your existing partitions. However, I recommend that you use a Windows disk manager/utility/thing to resize any NTFS or FAT partitions you have; using gparted on these partitions may cause filesystem corruption or data loss.

---

### Post by wildmanne39 on 2011-07-13
> **kedaar said:**
> Ok, I guess I should resize and reinstall, is there any instructions for doing this?

Thanks guys!hi, here is a guide for resizing partitions. It has to be done with a livecd.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by kedaar on 2011-07-23
Hi,

I dont have a cd drive on my laptop, I used the usb to install ubuntu.

Can I just use the same usb installer to delete sda3, sd4, and sd5 and then reinstall

---

### Post by drs305 on 2011-07-24
> **kedaar said:**
> 
Can I just use the same usb installer to delete sda3, sd4, and sd5 and then reinstall

Yes you can. Once you get to the Ubuntu Desktop it's all the same.

---


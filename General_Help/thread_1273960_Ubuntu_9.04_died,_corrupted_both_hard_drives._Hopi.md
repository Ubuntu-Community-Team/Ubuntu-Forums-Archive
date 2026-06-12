---
title: "Ubuntu 9.04 died, corrupted both hard drives. Hoping to repair."
date: 2009-09-24
forum: General Help
---

### Post by IsmAvatar on 2009-09-24
Sappy Background story, skip if you don't like reading:

Ubuntu really doesn't like me, and has clever ways of expressing it. Namely, it likes to screw up my hard drive. I have 2 hard drives - one for swap and Ubuntu (sata /dev/sda), and the other for data (sata /dev/sdb). Not too long ago, it took out my sda hard drive and I was never able to find it listed for mounting again, so I figured it must be totalled, so I went out and bought a new hard drive and replaced it, and all was good... for a month. Then one day I booted up and Ubuntu informed me that I had performed an unclean shutdown (even though I had shut down using the normal method - click on the logo, and click shutdown, etc). It then ran fsck and failed. I ran fsck /dev/sda5 (ubuntu partition), and it ran fine for a while. Until 2 boots later, when it did it again. It seemed to repeat this ritual every other boot, until today, when it finally called it quits altogether, and running fsck was ineffective.

More important background story

So I decided to reformat sda and reinstall Ubuntu (via LiveCD). I started to back up my data, and it worked fine for the most part, except one folder was giving obscure errors halfway through a file, so I just skipped that folder, since the data was unimportant. I then went through the install process, and told it to include sdb as /data, and continued. However it popped up an error message about some kind of IOError at <location_to_corrupted_file>, and that I'd need to run dosfsck on sdb.


```
ubuntu@ubuntu:/$ sudo dosfsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/ismavatar/Desktop/plugins
  Contains a free cluster (3978622). Assuming EOF.
/ismavatar/Desktop/EvolutionaryAnts.odp
  Contains a free cluster (3986931). Assuming EOF.
/ismavatar/Desktop/EvolutionaryAnts.odp
  File size is 415511 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/ismavatar/Desktop/enigma/plugins
  Contains a free cluster (3975911). Assuming EOF.
/ismavatar/Desktop/enigma/ENIGMAsystem
  Contains a free cluster (3975929). Assuming EOF.
/ismavatar/Desktop/enigma/CompilerSource
  Contains a free cluster (3976829). Assuming EOF.
/ismavatar/Desktop/enigma/.svn/props
  Contains a free cluster (3975761). Assuming EOF.
Read 32 bytes at 65382920192:Input/output error
ubuntu@ubuntu:/$ ls -Al /media/data/ismavatar/Desktop/enigma/.svn
ls: cannot access /media/data/ismavatar/Desktop/enigma/.svn/props: Input/output error
total 80
-rwxr-xr-x 1 root root   167 2009-09-10 05:37 all-wcprops
-rwxr-xr-x 1 root root   522 2009-09-10 05:37 entries
drwxr-xr-x 2 root root 16384 2009-09-10 05:36 prop-base
d????????? ? ?    ?        ?                ? props
drwxr-xr-x 2 root root 16384 2009-09-10 05:36 text-base
drwxr-xr-x 5 root root 16384 2009-09-10 05:37 tmp
ubuntu@ubuntu:/$ rm -rf /media/data/ismavatar/Desktop/enigma/.svn/props
rm: cannot remove `/media/data/ismavatar/Desktop/enigma/.svn/props': Input/output error
ubuntu@ubuntu:/$
```

So there you have it. I'm stuck with a corrupted file that I can't remove, and it's blocking me from installing Ubuntu.

Now what do I do?

---

### Post by theozzlives on 2009-09-24
Sounds like SDB has some bad sectors, might want to try a low level format (if they still make utilities to do that).

---

### Post by IsmAvatar on 2009-09-24
I'm unfamiliar with that. Since this is my data drive, and all of my data (sans that one file) is still perfectly accessible, I'd like to avoid formatting the drive. At least until I can get my data transferred to a backup medium.

That is, unless by "low level format" you mean formatting a specific section (namely where the corrupted file is), and leaving the rest of it untouched.
But again, I'm completely unfamiliar with that, and wouldn't know where to begin.

---

### Post by seadao on 2009-09-24
This happened to me every time i tried 9.04, i use a asus g1s and it works great for a little bit, but then it says partition is inconsistent, after checking it home folder is gone!! i have not found a solution to this but try testdisk, you might recover some data, i'm back on hardy because of this.

i would wait for 9.10...
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
i was smart to make a live cd of hardy with isoremaster all the tools like testdisk and gparted... it's a good practice if your trying new os, bleeding edge stuff

---

### Post by IsmAvatar on 2009-09-24
I had these issues with 8.10 as well. I specifically upgraded to Jaunty and ext3 (and eventually ext4) because it was supposed to get rid of these "unclean shutdown" problems.
I'm definitely looking forward to 9.10, but it won't do me a lot of good if I can't even install 9.04.

---

### Post by kfitzenreiter on 2009-09-24
My first inclination, since it involves two different hard drives is perhaps a bad motherboard.  I would first try a low-level format and/or the hard drive diagnostic tools you can download from seagate, western digital and or the other one I can't think of right now.
 
I suppose bad ram could always be an issue so it never hurts to run memtest too.  A bad power supply could also potentially cause problems as well.  You may want to try the hard drives in other pc's as slaves and see if they run properly.

---

### Post by seadao on 2009-09-24
> **kfitzenreiter said:**
> My first inclination, since it involves two different hard drives is perhaps a bad motherboard.  I would first try a low-level format and/or the hard drive diagnostic tools you can download from seagate, western digital and or the other one I can't think of right now.
 
I suppose bad ram could always be an issue so it never hurts to run memtest too.  A bad power supply could also potentially cause problems as well.  You may want to try the hard drives in other pc's as slaves and see if they run properly.


testdisk, is the most powerful easy and free tool i have ever used, it can recover most of your data, even from PREVIOUS and DELETED partitions give it a shot, seagate and western digital tools are mostly useless, and might make things worse (make testdisk recover less data later)

it helped me recover a seagate drive that didn't mount by giving me a superblock address, that you use with fsck to restore the disk,

I RECOVERED ALL MY DATA ON THAT DISK!!!!!!!!!!

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

i would try this program first it REALLY works!!

---

### Post by emeraldgirl08 on 2009-09-24
Why don't you recover the data you would like to keep via slave method? Extract those folders, files, etc and then Killdisk it.

I know when I do a reinstallation of my laptops recovery disks I HAVE TO HAVE A CLEAN DRIVE! If I do not have a clean drive I was warned that it would not work. This almost seems like a universal method to get the least problematic results.

---


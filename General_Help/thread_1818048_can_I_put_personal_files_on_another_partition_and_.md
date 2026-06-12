---
title: "can I put personal files on another partition and have it mount in /home?"
date: 2011-08-04
forum: General Help
---

### Post by ninjaaron on 2011-08-04
I've been playing around with stuff lately, and I was thinking that I could theoretically move my personal files to another partition, have it mount under /home/User... then change the system partition to 6 or 7GB and go about my merry way...

That way, if I need to reinstall the os, or when the next release comes out, or even install another primary system, I could just wipe the system partition and keep all my data on the HD...

just make an fstab entry like:

```
/dev/sda3    /home/User    btrfs   default  0  2
```

or something, and them BOOM! it's done. I am the master of my domain.

Would that work?

---

### Post by WhiteHorse on 2011-08-04
nope, you need to reformat the drive

---

### Post by tommpogg on 2011-08-04
> **WhiteHorse said:**
> nope, you need to reformat the drive

Why? It looks like it is gonna work: every time he reinstalls the OS he has just to modify /etc/fstab to have his data partition to be mounted automatically. Am I wrong?

---

### Post by ninjaaron on 2011-08-04
> **WhiteHorse said:**
> nope, you need to reformat the drive

Yeah, I think your wrong.  I'm going to try it right now.

---

### Post by tommpogg on 2011-08-04
> **ninjaaron said:**
> Yeah, I think your wrong.  I'm going to try it right now.

Ok. Please, give us a feedback when you have done it. I am planning to do the same thing

---

### Post by CatKiller on 2011-08-04
> **tommpogg said:**
> Why? It looks like it is gonna work: every time he reinstalls the OS he has just to modify /etc/fstab to have his data partition to be mounted automatically. Am I wrong?

Don't even need to do that. When you install you get to pick a partition to be mounted as /home.

 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ninjaaron on 2011-08-04
found a [page for it in the community documentation]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), basically saying to do what I said.

---

### Post by ninjaaron on 2011-08-04
> **CatKiller said:**
> Don't even need to do that. When you install you get to pick a partition to be mounted as /home.

 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Ah yes, but I am already installed, so I am migrating my stuff over.

---

### Post by spook1980 on 2011-08-04
you can mount it in a folder in your home folder that's easy

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mick.mdu on 2011-08-04
Assuming that the partition is formatted properly, there should be no issues with this working.

---

### Post by ninjaaron on 2011-08-04
Gave it a test-run on my netbook.  I forgot to copy the hidden files in my home folder, so my desktop wouldn't load. lulz.  Anyway, the files are there, so I'm doing a fresh install of the system. My data should theoretically still be there.  It's all backed up, but we'll see.  I just realized something else I did that might delete it all.

If I ever get it to work on my netbook, I'm gonna do it on my main computer.

---

### Post by CatKiller on 2011-08-04
> **ninjaaron said:**
> Ah yes, but I am already installed, so I am migrating my stuff over.

From the page I linked earlier:

> **Introduction**

 This guide is for creating a separate /home partition if you already installed Ubuntu *without* a /home partition (i.e., /home is just a folder inside your / partition).   Having a separate /home partition makes it easier for you to reinstall  Ubuntu while preserving your personal files and settings. This is a  matter of convenience but is not foolproof. You should still regularly  back up your data. 


---

### Post by ninjaaron on 2011-08-04
> **CatKiller said:**
> From the page I linked earlier:

Yeah, well I did it.  Took a long time, but it's done now.  I just 'followed my heart,' and now it's done. All that mucking about with /etc/fstab in Gentoo and Arch has paid off.

Anyway, for the guy who wanted to try it, don't forget to copy your hidden files. I did that with my netbook (for a test run.  Not much on there), and it broke my session, so I had to reinstall the system.  The data is still there, since it was on the other partition (which is proof of concept), but I had to reinstall my apps and ppa's, which was kinda a pain, but whatever.  It's a netbook, so there wasn't anything huge anyway. It's pretty much back to normal now.

Then I did it on my main computer, which took a long time, because I had 80GB of data on it (was more like 130 before, but took of all the movies, since I aready have them saved elsewhere).To do this, you must have as much free space on your drive as you have used, or you have to copy the data to a backup medium before you do it.  I did it without all on the drive (just so happens that everything is backed up also, but that's not the point).  This is because you have to have all the original data there while you copy it onto the new partition.

It would probably be faster to do it with a backup device, rather than all on one disk, since that way you are only copying the data twice, rather than three times. The third time is when you move the partition to take up all the space that old files were taking... your computer has to copy everything again at that point. It would be better to delete the files from your HD, then do all the partitioning, then move the files onto the correctly sized partitions, though it partially depends on the RW speeds of your internal disk and external storage medium.  Of course, it is preferable to have your data backed up anyway when you are doing all those partition modifications.  I've never actually lost anything doing them... except when I interrupted them (but all I lost those times were OSX and Windows7, so who cares?)

Anyway, I did all the copying of files on the live medium because I thought it would be better, since the system would never access the disc, and I could use the internet and whatever else I wanted while the HD worked undisturbed.  This meant that I had to copy everything with sudo. 

This is problematic. When I rebooted, all the permissions were root, which, again, broke my session, so I had to drop into the console and change the permissions to all the files.  If you do it this way, the command is:
```
sudo chown -R YourUserName /home
```
... obviously replacing YourUserName with your user name. I effing chowned those files...

Ok. That's it. Doing all this stuff takes a long, long time, but when it's done, it will save your data from system failures and allow you to migrate to another system no risk to the data, as well as allowing you to load your personal data into several different OS's rather easily (not that it was terribly difficult before).

---

### Post by oldfred on 2011-08-04
Some more info if you are interested after the fact.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by CatKiller on 2011-08-04
FWIW, tar preserves ownership in a way that cp/mv don't.

---


---
title: "Reducing partition size?"
date: 2010-02-20
forum: General Help
---

### Post by zippy_uk_2001 on 2010-02-20
Hi all, 

Quick question about partition sizing - or more to the point reducing a partition.

Got a nice fresh build running a dual boot windows/Koala. It's a 1.5tb drive, so I gave 500 to Windows (I promise I only use Windows for games ...honest) and the rest to Ubuntu.

But now I have burg running with it's shiny boot menu, I was thinking how nice it would be to have another OS on there (maybe play around with osx86 for example).
 
However, I didn't think to leave any spare space ...D'oh!

So, looking at the larger Ubuntu partition, can I now re-size that, so that I can give this potential new OS some room to play? 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54918   441125968+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           54919      182401  1024007197+   5  Extended
/dev/sda5           54919      182027  1021003011   83  Linux
/dev/sda6          182028      182401     3004123+  82  Linux swap / Solaris

(On another subject - is that cylinder note there something I should look at?)

I've got Gparted installed, but all the options for /dev/sda2 are ghosted ...which I kinda think may answer my question - but thought I would ask anyway :-)

It is a fresh build, so scrubbing and starting again would only be an annoyance rather than a problem - so that's my plan B

Any ideas or thoughts gratefully received 

Cheers,
Zippy

---

### Post by Girya on 2010-02-20
it sounds like you have sda2 mounted.

you need to use gparted from a live cd so all your partitions on the hard drive aren't mounted

---

### Post by Girya on 2010-02-20
it sounds like you have sda2 mounted.

you need to use gparted from a live cd so all your partitions on the hard drive aren't mounted

---

### Post by volkswagner on 2010-02-20
It will be difficult to unmount you running partition.  You will want to use a live cd to do the resize.

All partitions I have ever created with windows, show the same error complaining about cylinder boundry.

Once you reduce the size of you linux / partition, I would recommend leaving some free space for future installs...

Cheers.

---

### Post by cariboo on 2010-02-20
This really has nothing to do with server platforms, moved to General Help

---

### Post by zippy_uk_2001 on 2010-03-01
Completely forgot about the live CD - nice one, I'll give that a try.

Cheers 
Zippy

---

### Post by oldfred on 2010-03-01
Partition planning is important especially if installing multiple operating systems. If just installing Ubuntu many recommend the separate /home to make it easy to upgrade, but you cannot share /home (or any other partitions like /boot) with other installs. But you can easily share all your data which is most of the space you use.
I so far have just 3  20GB partitions for ubuntu, last install, current install and new beta for testing next install. When I set this up I did create a /home but it is only 1GB in a 50GB partition as I ended up creating the separate /data partition. I will eliminate the /home on the next update since I can easily backup a 1GB /home and reinstall on a new version. I hide the mount of /data and link everything into /home so all my data is easy to use.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
oldfred's versions
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by zippy_uk_2001 on 2010-03-08
Some nice links there - I feel a bit of learning coming on :-)

Thanks,
Ash

---


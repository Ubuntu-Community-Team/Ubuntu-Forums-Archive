---
title: "Installing packages when main HD/SSD is full"
date: 2011-02-21
forum: General Help
---

### Post by bjackman on 2011-02-21
I've been running Xubuntu 10.4 Lucid Lynx on a netbook. It's an EeePC 701 which has been upgraded to 2Gb RAM, but the only storage device is a soldered-in (why:confused:) 4Gb SSD. At present this prevents me from installing much software. I started a [COLOR=Blue][previous thread (link)]("http://ubuntuforums.org/showthread.php?t=1686097")[/COLOR] in Absolute Beginner Talk which pointed me to portablelinuxapps.org, where I found a list of applications that were compiled to a single executable that could be run from any locaton (inc. USB drives): absolutely brilliant for openoffice and skype etc, but it's still a limited list of software.

So I was wondering if theres any possibility to install conventional packages in a way that uses space on a different drive (i.e an SDHC card in this case)? I'm open to the possbility that this may mean keeping the card in at all times.
Alternatively, is it possible for an end-user to create the kind of self-contained executables found on portablelinuxapps.org, or can only the developer do it?

Thanks!

---

### Post by veggen on 2011-02-21
I was wondering the same thing many a time... The only idea I have (haven't ever tried it) is to find where the installed files usually go (I presume /usr/<something>) and make that directory a mount point for another device. I think that's how Linux's virtual file system is meant to work... you plug different physical file systems into VFS's different branches.

---

### Post by veggen on 2011-02-21
Very strange that no one else has any input on this...

---

### Post by wiggly81 on 2011-02-21
you could use an external HDD / USB thumb drive and create a partition with a mount point /usr copy all your data from original /usr directory, i used this method in the past for my /home directory.
you could do it with as many mount points as you want i guess

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

that helped me with my /home i guess its much the same for any other mount point

if im missing the point im sorry but i do hope this is of some help

---

### Post by bjackman on 2011-02-22
[COLOR=DimGray]Ah yes this does seem like a good idea. The idea did come to me as I pondered, but i shrugged it off thinking it sounded ambitious, but the more I read, the more it seems anything's possible in Ubuntu:P. I'm starting to see why people love linux so much! I'll do a bit of research and see if I can pull it off, and report back here in case anyone's interested.[/COLOR]

edit: hmm, I was confused, for some reason I thought that the application binaries were stored conveniently in /home, but now I see they clearly aren't! Building on what Veggen said, I guess theyre stored in /usr/bin - maybe it's possible to set that as a mount point for my SDHC card. I think this issue needs another thread where maybe I can find some more specific advice.

---

### Post by veggen on 2011-02-22
/home/<username> has the user specific configs only. Since apps need to be usable by all users, they're stored under /usr/. Also, I believe that not all apps go the same directory nor that all app files go to a single place, I think the best thing to do would be to move the content of the whole /usr/ directory to an external device and then mount it in the same point (/usr/). Doesn't sound too hard, but... couldn't say for sure. Haven't tried it.

---


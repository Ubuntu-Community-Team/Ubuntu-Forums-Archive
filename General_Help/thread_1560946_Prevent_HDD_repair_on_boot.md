---
title: "Prevent HDD repair on boot"
date: 2010-08-25
forum: General Help
---

### Post by SuperDuckk on 2010-08-25
Hey guys, I installed Ubuntu to use ddrescue to clone my dying drive and keep the log.

Now the question is:
Does Ubuntu really try to repair a corrupt NTFS disk during boot?
If so, how can I change this behaviour, including any disks attached to the system in future?

I had a similar question for the live cd, I think it should be easier now, as we can configure the system.

Btw am I the only one to think an 'auto repair' by default is no good without asking for permission? It's something I dislike on Windows. A corrupt structure is likely a hardware problem, and in this case a repair can terribly damage the file system.

---

### Post by dabl on 2010-08-25
> **SuperDuckk said:**
> 

Does Ubuntu really try to repair a corrupt NTFS disk during boot?



No.

AFAIK, this is still the current status of ntfsprogs' file system checking capability:  [http://www.linux-ntfs.org/doku.php?id=ntfsck](http://www.linux-ntfs.org/doku.php?id=ntfsck)

Also, I'm not sure why you would choose Ubuntu for that particular problem (failing hdd, data rescue) when you could use something like this:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by SuperDuckk on 2010-08-25
Thanks for the info Dabl.

> **dabl said:**
> 
I'm not sure why you would choose Ubuntu for that particular problem (failing hdd, data rescue) when you could use something like this:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Well, I'm not sure about how well other projects like 'systembootcd' or 'clonezilla' are maintained and how current their drivers / kernels are. I've found a bunch of live repair disks and even some of them are maintained by single person. This makes better sense considering I also want to keep recovery specific data on the disk, like log files, and also want to keep Ubuntu for various use, though I already keep an installation on a virtual box. I may also need to install additional packages, like I did with the most recent version of ddrescue for Ubuntu, and would like to keep packages I work with, rather than setting everything up again and again after each boot. I intent to make a few passes in different boot sessions.

---


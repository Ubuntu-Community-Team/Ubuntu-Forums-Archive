---
title: "SMART bad sectors notification"
date: 2009-11-12
forum: General Help
---

### Post by rekahsoft on 2009-11-12
Hi all, i'm running ubuntu 9.10 and just received a error from a program named "Palimpsest" saying that a hard drive has gone bad..thing is its pretty much brand new...its a seagate barracuda 7200 rpm 1TB drive...the error reported is as follows:

Reallocated Sector Count: 57
Airflow Temperature: 56* C / 133* F

..if you would like more details i would be happy to get them...i am just unsure of where to look..

---

### Post by lavinog on 2009-11-12
see my post here:[http://ubuntuforums.org/showpost.php?p=8306209&postcount=55](http://ubuntuforums.org/showpost.php?p=8306209&postcount=55)

your reallocated sector count is really low, and shouldn't be an issue.

There is a couple of bug reports about this issue.

---

### Post by Mark Phelps on 2009-11-12
Just to be safe, I would run fsck against all of your partitions.  If no errors are found, this is yet another case of "false positives" in 9.10.

---

### Post by toxicpoison on 2009-11-12
> **rekahsoft said:**
> Hi all, i'm running ubuntu 9.10 and just received a error from a program named "Palimpsest" saying that a hard drive has gone bad..thing is its pretty much brand new...its a seagate barracuda 7200 rpm 1TB drive...the error reported is as follows:

Reallocated Sector Count: 57
Airflow Temperature: 56* C / 133* F

..if you would like more details i would be happy to get them...i am just unsure of where to look..


think thats just a clitch that will be remidied in the future, got the same thing saying iminent harddrive failure on not just 1 new harddrive but 2 harddrives out of the box,

---

### Post by fluffman86 on 2009-11-12
I got the same error.  It's probably a false positive, but a good reminder to always have backups. ;)

If you don't have a live CD handy to fsck with, you can force a fsck on the next boot by running
```
sudo touch /forcefsck
```
in Applications > Accessories > Terminal and rebooting.

---

### Post by fluffman86 on 2009-11-12
> **toxicpoison said:**
> think thats just a clitch that will be remidied in the future, got the same thing saying iminent harddrive failure on not just 1 new harddrive but 2 harddrives out of the box,

Yeah, I've never had much luck with the SMART tools regarding hard drive health.  They're great for testing what's going on *now* though, just not predictive stuff.

---

### Post by lavinog on 2009-11-13
> **Mark Phelps said:**
> Just to be safe, I would run fsck against all of your partitions.  If no errors are found, this is yet another case of "false positives" in 9.10.

fsck does not check for bad sectors the same way SMART does.  Sector relocation happens transparently.

Ex:
lets say sector 5 is bad, the firmware detects this and reallocates this to sector 1005.  Now every time a request is made by the os to access sector 5, the firmware accesses 1005, and the OS will continue to think that sector 5 exists.

---


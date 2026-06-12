---
title: "viruses with Wine"
date: 2010-02-22
forum: General Help
---

### Post by anaconda on 2010-02-22
****..
I have been running one windows program in wine for some time now.
Yesterday I installed a copy of it to a windows machine and I found out it has a couple of Trojans in it!!

Should I be worried? 

BTW. I found an interesting thread about wine viruses
[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

I got a bit worried. 
the "/" root partition is mounted by default in wine, (WHY?!?!) so a bad windows virus has access to and could destroy (or infect) everything in my home folder and on my external hd:s data partition, and everywhere the normal user has full rw permissions... And wine programs also have access to internet, so viruses can also download/upload anything...

?????

And I thought I was safe from windows viruses.... Damn.

Why an earth is the root partition mounted by default in wine???? It is a real security risk.

When I get back home I will scan my ubuntu. Hope I dont find anything...

---

### Post by 3rdalbum on 2010-02-22
Windows viruses don't understand the filesystem hierarchy of Linux, so they're not likely to know to go to /media/disk to infect external hard drives. They also can't modify anything inside / unless you run Wine as root, which is severely not recommended.

Wine is a calculated security risk anyway; it's only as secure as the software you run on it, which in your case might be nil. But be aware that some programs will be flagged in some anti-virus programs, but don't actually contain malware (just something that has a similar signature). Check what your anti-virus program actually says about the software.

---


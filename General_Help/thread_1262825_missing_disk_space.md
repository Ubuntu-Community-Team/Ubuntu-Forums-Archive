---
title: "missing disk space"
date: 2009-09-10
forum: General Help
---

### Post by dmitriyp13 on 2009-09-10
Ok, here's the deal. I'm getting an out of disk space error.  

'df -h' tells me I'm completely out of space on '/'.  But for the life of me I can't figure out who's using it.  I tried baobab and nautilus.  I've been able to account for 18GB out of 29GB on the partition but I can't account for the other 11GB.  

Any ideas?

---

### Post by tomBorgia on 2009-09-10
Have you tried the disk usage analyser tool? Applications > Accessories > Disk Usage Analyser

---

### Post by hwttdz on 2009-09-10
sudo du / --max-depth 1 -h

Might give you a place to start looking.  Granted you're probably going to want to investigate at a deeper level.  Maybe look at the home directories, and see if there's a lot of space disappearing there, replace "/" with "/home/".  Good luck.

---

### Post by DaithiF on 2009-09-10
Hi,
if/when you have exhausted the 'du' approach, and if there remains a discrepancy between the free space reported by df vs the usage you can account for using du, then take a look at this thread for one possible cause:
[http://ubuntuforums.org/showthread.php?t=1251827](http://ubuntuforums.org/showthread.php?t=1251827)

---

### Post by nikhilbhardwaj on 2009-09-10
you could see how much space is taken by the /var
the logs and package cache etc are stored here
if it is unusually high
then perhaps you can clean up some things from there
never ever do rm -rf /var though

---

### Post by drs305 on 2009-09-10
I wrote a fairly comprehensive guide on tracking down lost free space. Here is the link:
[HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

GUI and terminal commands are both covered.

If you have questions from the guide, post them here.

Most likely culprits: backups to the wrong location, large log files, and undeleted root trash.

---

### Post by dmitriyp13 on 2009-09-10
Thanks for the help everyone.  I found the problem but I'm not 100% sure what caused it.  I have a large partition mounted to '/storage' where I keep all of my backups.  Yesterday, it was unmounted while my backup job ran.  I think it ended up dumping all of those files onto '/' instead.  It was approximately ~18GB worth.

---


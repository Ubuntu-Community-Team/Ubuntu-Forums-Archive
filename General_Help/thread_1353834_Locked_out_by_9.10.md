---
title: "Locked out by 9.10"
date: 2009-12-13
forum: General Help
---

### Post by Draigcoch on 2009-12-13
When I installed Ubuntu 9.10 there were no initial problems.  However after a few updates I was presented with a brown login screen.  I duly entered my password but it was frequently rejected.  After 6 or 7 tries it worked.  Today 14 attempts have been without success.

Looks like I will have to re-install 9.04.  Trouble is I will lose a week's work currently held in a file on the desktop.  Anybody know how to extract this file/folder?:(

---

### Post by gslug79 on 2009-12-13
Hi

If you have a separate /home partition, your work will be unaffected by a reinstall. Choose advanced in the partitioning section of the installer, select the existing / partition and reuse this as / (and format it). Do the same for /home but DO NOT formt it.

If /home is not separate, boot off the live CD and mount the hard disk. In Nautilus this will be under "Computer" and will be called something like 500GB Volume. Mount this, navigate to your home folder, then Desktop. Find the files/folders that you want to keep and copy them to another storage medium, a USB key for example.

It is always useful to have /home on it's own partition as no mater how badly you break an install, you can always reinstall and keep your data.

---

### Post by Draigcoch on 2009-12-13
Kevin - thanx for the info but I managed to log on a few minutes ago.

To start I was presented with that horrible brown screen.  I did a restart (on the computer's button) and this time I got the proper screen.  All files now copied to backup.  

Am still going to dump 9.10 and re-install 9.04.  Here's hoping an update doesn't mess that up too!

Thanx again.

---


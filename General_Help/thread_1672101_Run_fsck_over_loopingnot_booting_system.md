---
title: "Run fsck over looping/not booting system"
date: 2011-01-20
forum: General Help
---

### Post by pharubu on 2011-01-20
**CONTINUATION ON FROM THREAD:**
[http://art.ubuntuforums.org/showthread.php?t=67223](http://art.ubuntuforums.org/showthread.php?t=67223)


**ERROR**

* Activating swap [fail]
* Checking root file system
fsck 1.40.8 
/dev/shm/root contains a file system with errors, check forced.

/dev/shm/root:
Inodes that were part of a corrupted orphan linked list found.

/dev/shm/root: UNEXPECTED INCONSISTENCY; RUN fsck manually without -a or -p options 
fsck died with ext status 4

An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted
The fsck should be performed in maintenance mode with the root
filesystem mounted in read-only mode.


The root filesystem is currently mounted in read-only mode.
a maintenance shell will now be started
after performing system maintenance pres control d
give root password for maintenance


**FIX**
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Download: ADRIANE-KNOPPIX_V6.2.1CD-2010-01-31-EN.iso

Load CD using BIOS or vmware settings
From main Menu: filesystem / devices, ESC 
From main Menu: command / shell, fsck /dev/sda1

With VMWARE you could alternatively:
- stop antoher running image
- vmware settings: load corrupted image as slave 
- start; run fsck
- stop; reset settings; restart both images

---


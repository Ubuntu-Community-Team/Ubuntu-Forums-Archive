---
title: "how do you stop automount an external USB drive"
date: 2010-01-17
forum: General Help
---

### Post by johnnynb on 2010-01-17
Everyone seems to what to know how to automount an external USB drive.
I'm trying to stop 9.10 from automounting it. Normally I use fstab
to mount an external drive where I prefer it to be mounted. But after
the last software update karmic (9.10) is now automounting my drive
and screwing up the fstab mount 

Some how the drive is showing up as /dev/hdd1 and /dev/hde1. 

I could just shutoff automount but I like it for USB sticks and cameras 
and MP3 players.  

How do you stop automount from mounting just an exteral USB drive??

---

### Post by drs305 on 2010-01-17
Since you are familiar with fstab, why not add an entry for the external device, identified by UUID, and using the "noauto" option?

---

### Post by johnnynb on 2010-02-02
I found the answer to this problem.  I changed fstab to refer to the 
drive by its UUID instead of /dev/sdd1 name.  My Karmic Koala auto-magically
now mounts the disk in the file system where I want it.

You can use the "blkid" command to find the UUID for the device.

---

### Post by Grenage on 2010-02-02
Yup, if you are referencing a specific device it's always best to use UUID. Consider common names to be dynamic.

---


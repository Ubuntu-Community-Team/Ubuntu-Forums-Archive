---
title: "Problems reading data DVDs"
date: 2006-05-10
forum: General Help
---

### Post by Dr. Feelgood on 2006-05-10
For some reason, my computer can't read some data DVD's that it used to be able to read before the switch to Ubuntu.  They are DVD+R's that have Mp3's or Videos.  I put them in and basically they are either not recognized and never mounted or it's mounted and I get nothing but three or four files named "?????????????????" or stuff like that.  What drivers do I need or what settings do I have to fix.  I used to read them fine on the same computer under a different OS.

---

### Post by an.echte.trilingue on 2006-05-24
Have you tried mounting them from the command line?
```

mount /dev/cdrom /media/cdrom
cd /media/cdrom
ls
```

---

### Post by Dr. Feelgood on 2006-05-24
When I enter that into terminal it says I need to specify a filesystem.  I tried changing directories to /media/cdrom anyways and it worked but ls turned up nothing as well as ls -a.  The DVD works on another computer (windows xp).  I'm wondering whats the missing link.  The DVD that gave the files with "???????????" actually started working after mounting and unmounting them a few times though.

---


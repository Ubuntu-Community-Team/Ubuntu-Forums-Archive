---
title: "kernel modules built but not loaded at next startup"
date: 2009-10-28
forum: General Help
---

### Post by cnbiz850 on 2009-10-28
I installed VirtualBox on Karmic 64bits.  It works OK.  But next time I start the computer and start VBox, it says something like kernel driver not loaded rc=-1908.  I checked with lsmod and found the vbox related modules are not there.  So, I did ```
sudo /etc/init.d/vboxdrv setup
``` to rebuild it and it works OK.  But the problem is that at next startup the modules are not loaded either and I have to rebuild it.

Anyone please advise what best to do.

---

### Post by cnbiz850 on 2009-10-28
OK, I had to do this:
sudo modprobe -v vboxdrv
then it is fine at the next start.

---

### Post by cnbiz850 on 2009-10-28
OK, I had to do this:
sudo modprobe -v vboxdrv
then it is fine at the next start.

---

### Post by cnbiz850 on 2009-10-29
Well, that doesn't really work.  For some reason, after restart the kernel modules are not loaded.

Now some easier thing to do, I run the following after login:

sudo /etc/init.d/vboxdrv start

Any better ideas please?

---

### Post by cnbiz850 on 2009-11-05
Solved as according to [http://ubuntuforums.org/showpost.php?p=8247245&postcount=2]("http://ubuntuforums.org/showpost.php?p=8247245&postcount=2")

---


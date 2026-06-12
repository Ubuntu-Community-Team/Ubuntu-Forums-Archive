---
title: "Storage Media Issue"
date: 2006-02-25
forum: General Help
---

### Post by patsissons on 2006-02-25
There are times when I cannot properly eject my ipod (using sudo eject /dev/sdX) and when this happens, if I plug it back in before restarting, the new device node will be /dev/sd(X+1) where where sd(X+1) is the next letter in the alphabet.  Although not a very pressing issue, it is stil annoying none the less.  Im just wondering if there is a way to force this module to reset back to sda?  I believe the module responsible is kio, but thats just a guess.  any thoughts on this?  :confused:

---

### Post by patsissons on 2006-03-03
Just an update on this, I think that I figured it out.  I can't confirm this yet, but it seems makedev is responsible for this behaviour.  I tried out `sudo /etc/init.d/makedev restart` and my ipod was once again mounted to sda.  So it appears that this is a possible quick fix to this issue.

---


---
title: "Upgraded to 11.10, lost a hard drive"
date: 2012-09-30
forum: General Help
---

### Post by abelundercity on 2012-09-30
The drive that I had originally installed with the help of [this thread]("http://ubuntuforums.org/showthread.php?t=2031238") seems to have gone missing upon upgrade to 11.10.  I'm rather keen to get the system to find it again, as you might imagine.

Any advice?

---

### Post by Bashing-om on 2012-09-30
First place I would check is /etc/fstab ...verify that any entry corresponds with blkid .

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by abelundercity on 2012-10-04
OK, I found the trouble.  "mnt" was set to root and wasn't giving me access to the "data" folder.  Everything is where it should be now.

---


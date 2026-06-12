---
title: "Easy cd drive busy detection"
date: 2011-11-30
forum: General Help
---

### Post by Sith Lord Kyle on 2011-11-30
Odd title.  But I was wondering if anyone knew of a bash script or command that could tell without using mount/unmount that a cd drive was currently busy.  Preferably with output for additional functionality.

---

### Post by psad on 2011-11-30
Try this

#lsof|grep '/media/cdrom'

and replace  '/media/cdrom' by your cdrom mount point
No output means cdrom is  not in use.
Output will tell you what program is using files on cdrom. 

 Regards
pawel sadowski

---

### Post by Sith Lord Kyle on 2011-11-30
Weirdly, if I run that, terminal just brings me nothing.  If I run lsof by itself, I can find the drive running a program.  But it doesn't pull up anything when using grep.

---


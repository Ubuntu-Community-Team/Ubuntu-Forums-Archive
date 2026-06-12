---
title: "Any open source utilities for repairing bad sectors"
date: 2010-07-18
forum: General Help
---

### Post by cptrohn on 2010-07-18
On a Hard Drive that anybody knows of?  I have done some searching and I find some stuff for Windows... but not much for OS...

---

### Post by bumanie on 2010-07-18
If you know the drive manufacturer, you should go to their site and download their diagnostic tool (Free, open source, usually). If you are lucky, the diagnostic tool, may be able to remap the bad sectors, but it is likely that the drive is on its way out. Try the diagnostic tool and then if it shows there are heaps of bad sectors, retrieve everything you can from the drive before it fails for good. 
ddrescue is a possibility - it tries to read bad sectors and get as much info as it can, unlike the regular dd which will stop when it comes across bad sectors, ddrescue will keep going and then go back to the bad sectors and try to read them again. Start with the drive manufacturer diagnostic tool.

---

### Post by ronnielsen1 on 2010-07-18
Hirens bootcd has a lot of hard drive utilities

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

---

### Post by MooPi on 2010-07-18
The live cd also has some simple tools. Gparted can check your file structure. You can also use terminal apps, e2fsck is a great CL utility.Also ntfsprogs holds lots of promise for ntfs systems.

---

### Post by cptrohn on 2010-07-18
Thanks for the info!

---


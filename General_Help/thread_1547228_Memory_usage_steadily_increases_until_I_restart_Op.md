---
title: "Memory usage steadily increases until I restart OpenGL apps"
date: 2010-08-06
forum: General Help
---

### Post by Zorgoth on 2010-08-06
I use an ATI card with proprietary drivers and my memory usage in ideal situations when idle is around 600-700 MB.  I use cairo-dock, AWN, compiz, gnome-do, and GNOME (w/o panel).  My problem is, I have mysteriously increasing memory usage over time, which drops back down after I restart all my openGL applications.  It can get as high as 1.5 GB.  Looking in top, the weird thing is that when I sort by memory, I observe that none of the applications I am restarting, nor Xorg, use a significantly smaller percentage of system memory after being restarted.  So what is going on?  Does fglrx have some kind of memory leak?  And is there a fix?  In the last 10 minutes, my memory has for no apparent reason increased from 700 MB idle to 775 idle, and is still going up...

---

### Post by Zorgoth on 2010-08-07
bump?

---

### Post by caribo on 2010-08-22
I have had a similar problem for months now. using ATI radeon 7500, open source ATI driver, xorg 1.9 (xorg-edgers ppa) , KMS, compiz Ubuntu Maverick....

System is OK if I disable compiz... or disable KMS...

top shows nothing abnormal.. nor does /proc/meminfo. Cannot seem to pinpoint where the memory has gone, but suspect a kernal or ati driver problem...

sorry I cannot help... 

anyone else seeing this??

---


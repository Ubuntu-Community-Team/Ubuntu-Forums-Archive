---
title: "Applications start, then disappear?"
date: 2006-03-21
forum: General Help
---

### Post by MetalMike on 2006-03-21
I just installed a whole pile of applications with Automatix and promptly rebooted the system. Now when I try to launch some of these applications (FrostWire, NVIDIA Settings) it loads the taskbar button, the busy icon appears next to the mouse but then...nothing. Where does it go?

---

### Post by arnieboy on 2006-03-21
from terminal do the following:
```
frostwire
```
and paste the debugging output here.

---

### Post by MetalMike on 2006-03-21
```
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
```

I guess I need Java. :)

---


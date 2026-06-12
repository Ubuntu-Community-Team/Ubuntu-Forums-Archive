---
title: "The 3d Efects Crashing Pc"
date: 2009-09-05
forum: General Help
---

### Post by madman100 on 2009-09-05
Hi all when turning on the desktop 3d effects i get lockup and the system crashes a lot i have nvidia  8500gt when i disable the 3d effects and awn and compiz  i do not have any problems with lockup or crashing does any one know to to fix this problem

Thanks 
Madman100

---

### Post by Sam Lars on 2009-09-07
If you run
```
compiz --replace
```
from a command line, what is the output?

---

### Post by madman100 on 2009-09-09
Hi Sam Lars this is what i get when i run compiz --replace from the command line 

rich@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Thanks 
Madman100

---

### Post by Sam Lars on 2009-09-14
How did you install the drivers for your card?

---

### Post by madman100 on 2009-09-15
Hi yes it did install the drivers it all fix now and working turn some features in the BIOS and that seems to have done the trick 


Thanks
madman100

---


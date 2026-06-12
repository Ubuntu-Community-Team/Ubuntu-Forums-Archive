---
title: "help!!!"
date: 2009-10-13
forum: General Help
---

### Post by justincrediblee on 2009-10-13
okay so I unrestricted my graphics driver restarted my computer. and my cool desktop graphics wont show up...it says desktop effects could not be loaded.... I went in to a terminal and typed in compiz and here is the results........also I have a ati/amd proprietary fglrx graphics driver......


Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Rich_Roast on 2009-10-13
Does Xorg.0.log report anything?

```
grep '(EE)' /var/log/Xorg.0.log
grep '(WW)' /var/log/Xorg.0.log
```

---


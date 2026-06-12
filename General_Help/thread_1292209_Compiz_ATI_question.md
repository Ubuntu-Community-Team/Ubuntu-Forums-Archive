---
title: "Compiz ATI question"
date: 2009-10-15
forum: General Help
---

### Post by thecow on 2009-10-15
```
compiz --version
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
compiz 0.8.3

```

So as you can see it seems like hardware rendering is not available, I have a mobile X700 in this laptop.  This is a fresh install of Karmic, so do I need to install proprietary drivers from ATI?  I cant run Cairo dock because OpenGl does not display properly, I cant even run the non-OpenGl version properly however.  Would new drivers help this situation?

Thank you for your time

---

### Post by P4man on 2009-10-16
your videocard is no longer supported by ATI, so do not try binary drivers, as they won't work. That said, the opensource ATI drivers should enable compiz on that machine afaik. Can you post your xorg.conf ?

---


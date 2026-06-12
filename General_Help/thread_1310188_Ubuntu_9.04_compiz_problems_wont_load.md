---
title: "Ubuntu 9.04 compiz problems wont load"
date: 2009-11-01
forum: General Help
---

### Post by JewFro297 on 2009-11-01
on a dell dimension 3000 compiz wont load. intel integrated graphics. first time i try to run it here is the output:

```
fatchick@fatchick-desktop ~ $ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
Fontconfig error: "/etc/fonts/conf.d/30-cjk-aliases.conf", line 1: no element found

```

then to get to other windows i have to type exit twice to get out of the terminal. then there is no title bar and no maximize minimize etc buttons. heres what happens the 2nd time:
```

fatchick@fatchick-desktop ~ $ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
Fontconfig error: "/etc/fonts/conf.d/30-cjk-aliases.conf", line 1: no element found


```

then metacity loads and the windows go back to normal, but still no compiz effects.

---


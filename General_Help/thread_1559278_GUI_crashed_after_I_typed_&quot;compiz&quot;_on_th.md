---
title: "GUI crashed after I typed &quot;compiz&quot; on the shell"
date: 2010-08-23
forum: General Help
---

### Post by anirudhtomer on 2010-08-23
Hi all,

I was trying to run CompizConfig utility from my shell.
So I just wrote "compiz" on my shell & pressed enter & everything crashed with a black screen...I pressed some buttons and after a few seconds a disturbed GUI was there ...no buttons to close the window & no boundaries for all the windows that were open & most of the things were not working when I clicked on them.

I have managed to copy what happened on my shell

```
anirudh@anirudh-laptop: ~  [497] : $ > compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
^C
anirudh@anirudh-laptop: ~  [498] : $ >
```Can anyone help me on this issue. :?:

---

### Post by LowSky on 2010-08-23
To fix open a terminal and type

```
metacity --replace &
```

---


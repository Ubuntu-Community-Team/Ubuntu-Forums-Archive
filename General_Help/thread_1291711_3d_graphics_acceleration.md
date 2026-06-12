---
title: "3d graphics acceleration"
date: 2009-10-15
forum: General Help
---

### Post by chaotzu on 2009-10-15
When I'm starting steam it tells me that 3d graphics acceleration is not enabled. I'm not sure how to enable it though. The few tutorials I could find to help me with the problem told me to change the nvidia-xconfig file but when I open it it's blank. 

Any help would be appreciated thanks.

---

### Post by JigglyWiggly_ on 2009-10-15
What happens if you type compiz in a terminal?

---

### Post by chaotzu on 2009-10-15
I got the screen to flash and this in the terminal

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (2720x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

### Post by chaotzu on 2009-10-15
bump for help please!

---


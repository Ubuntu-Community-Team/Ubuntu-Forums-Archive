---
title: "compiz error.. bottom panel disappeared"
date: 2009-11-15
forum: General Help
---

### Post by xxhopingtearsxx on 2009-11-15
All I did was type "compiz" so I could get it to launch, and everything vanished except my wallpaper. Then my windows that I had oepned, things on the desktop, and etc showed up except the bottom panel. I don't care much about that, but I'm wondering why I Couldn't get COmpiz to load.

```
joey@ubuntu:~$ compiz
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
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
[ERROR]: Option "edge_flip_pointer" already defined
[ERROR]: Option "edge_flip_window" already defined
[ERROR]: Option "edge_flip_dnd" already defined
[ERROR]: Option "flip_time" already defined
[ERROR]: Option "raise_on_rotate" already defined
[ERROR]: Option "initiate_button" already defined
[ERROR]: Option "rotate_left_key" already defined
[ERROR]: Option "rotate_left_button" already defined
[ERROR]: Option "rotate_right_key" already defined
[ERROR]: Option "rotate_right_button" already defined
[ERROR]: Option "rotate_left_window_key" already defined
[ERROR]: Option "rotate_left_window_button" already defined
[ERROR]: Option "rotate_right_window_key" already defined
[ERROR]: Option "rotate_right_window_button" already defined
[ERROR]: Option "rotate_to_key" already defined
[ERROR]: Option "rotate_window_key" already defined
[ERROR]: Option "rotate_flip_left_edge" already defined
[ERROR]: Option "rotate_flip_right_edge" already defined
[ERROR]: Option "rotate_to_1_key" already defined
[ERROR]: Option "rotate_to_2_key" already defined
[ERROR]: Option "rotate_to_3_key" already defined
[ERROR]: Option "rotate_to_4_key" already defined
[ERROR]: Option "rotate_to_5_key" already defined
[ERROR]: Option "rotate_to_6_key" already defined
[ERROR]: Option "rotate_to_7_key" already defined
[ERROR]: Option "rotate_to_8_key" already defined
[ERROR]: Option "rotate_to_9_key" already defined
[ERROR]: Option "rotate_to_10_key" already defined
[ERROR]: Option "rotate_to_11_key" already defined
[ERROR]: Option "rotate_to_12_key" already defined
[ERROR]: Option "rotate_to_1_window_key" already defined
[ERROR]: Option "rotate_to_2_window_key" already defined
[ERROR]: Option "rotate_to_3_window_key" already defined
[ERROR]: Option "rotate_to_4_window_key" already defined
[ERROR]: Option "rotate_to_5_window_key" already defined
[ERROR]: Option "rotate_to_6_window_key" already defined
[ERROR]: Option "rotate_to_7_window_key" already defined
[ERROR]: Option "rotate_to_8_window_key" already defined
[ERROR]: Option "rotate_to_9_window_key" already defined
[ERROR]: Option "rotate_to_10_window_key" already defined
[ERROR]: Option "rotate_to_11_window_key" already defined
[ERROR]: Option "rotate_to_12_window_key" already defined
[ERROR]: Option "invert_y" already defined
[ERROR]: Option "sensitivity" already defined
[ERROR]: Option "acceleration" already defined
[ERROR]: Option "snap_top" already defined
[ERROR]: Option "snap_bottom" already defined
[ERROR]: Option "speed" already defined
[ERROR]: Option "timestep" already defined
[ERROR]: Option "zoom" already defined

```

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
Try ```
compiz --replace
```

---


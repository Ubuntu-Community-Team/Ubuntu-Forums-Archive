---
title: "how to stop blender from crashing ?"
date: 2010-01-14
forum: General Help
---

### Post by xieu90 on 2010-01-14
hi everyone
somehow my blender crash quite often.
(just scale something (change the size of an object) might make my laptop crash)
I saw in the system monitor applet that the IOWait go up to 100%, and it freezes my laptop.

here are all I have before and when it crashed.

my laptop is Lenovo SL500
core 2 duo T5870 2Ghz
1 GB ram
Intel Graphics media accelerator GMA 4500


oem@oem-laptop ~ $ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

oem@oem-laptop ~ $ blender -d
Blender 2.49 (sub 2) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.6.4rc2.
Checking for installed Python... got it!
Color depth r 8 g 8 b 8
Aux buffers: 0
read file 
  Version 247 sub 5
read file /home/oem/.B.blend
  Version 249 sub 2

ordered
 OBCube
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/oem/.blender/Bpymenus

Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBLamp
 OBCamera
Color depth r 8 g 8 b 8
Aux buffers: 0

ordered
 OBMesh
 OBLamp
 OBCamera
Killed


(I pressed CTRL ALT F1 and logged in then i used sudo htop to kill blender-bin)

---

### Post by xieu90 on 2010-01-30
yeah
and when it crash then that iowait go up
and my hdd will be used, the led of my hdd blink a lot or stay on all time, until I kill blender.

what could the problem be ?
any idea ?

---

### Post by pbrane on 2010-01-30
Are you sure blender has crashed? Some operations take a lot of time to complete. Especially if the operation is script controlled. The number of vertices can effect that too.

---

### Post by xieu90 on 2010-01-30
well
blender didnt really crash, but it froze the whole system.
and I tried to wait for it (30 minutes?)
and my cpu was idle (it didnt produce the hot air)

and I have just found out that when I do something in blender then the cache thing in memory will go up 
and then my hdd starts to run and iowait go up
and the whole system will be in matrix

may be i dont have enough ram ?

yeah, and all I did is only total beginner level. there arent a lot of vertices, and I have no idea how to write script, so I dont use script (yet)
just rotate a bit could make my computer frozen

---

### Post by pbrane on 2010-01-30
That's obviously not normal. I use blender with large number of verts and I have 2Gb RAM. I also have an nvidia 8600. Mabye there is an issue with the intel graphics?

Have you looked at blender's opengl settings under user preferences? Maybe you can tweak some settings.

---

### Post by xieu90 on 2010-01-31
> **pbrane said:**
> That's obviously not normal. I use blender with large number of verts and I have 2Gb RAM. I also have an nvidia 8600. Mabye there is an issue with the intel graphics?

Have you looked at blender's opengl settings under user preferences? Maybe you can tweak some settings.

did you mean that opengl where my mouse is ?
I havent tweaked it yet. Can you give me your setting ?

I also have another computer which have ati card(256mb ram) and 1,5 Gb (500 mb bigger ) ram. and Blender works well with it.

so I think that the problem might be 1 gb ram on my laptop (-384 mb for intel graphics) or the intel graphics itself.

I just know that when I do something then the cache will go up and then iowait and my hdd will run and the whole system will be in the dark winter. ^^

---


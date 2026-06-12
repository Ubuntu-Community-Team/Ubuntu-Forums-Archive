---
title: "nvidia xorg woes   couldn't find RGB GLX visual or fbconfig"
date: 2009-08-31
forum: General Help
---

### Post by krishnamo on 2009-08-31
I have recently installed NVIDIA driver (185.18.36) package in my laptop sony vaio VGN-Z12GN (hybrid graphics) on jaunty. The laptop has both intel and nvidia graphics  cards as follows 

lspci |grep VGA shows:
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)

Jaunty Linux Kernel is  2.6.28-15-generic

After nvidia driver installation X works fine.
"lsmod |grep nvidia"  shows 
nvidia               9594888  2 
agpgart                42696  3 intel_agp,nvidia

But I cannot work with some applications in X like pymol

 $pymol
 Xlib:  extension "GLX" missing on display ":0.0".
freeglut (pymol): OpenGL GLX extension not supported by display ':0.0'
 PyMOL: abrupt program termination.

glxinfo  says 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
2 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault



$dmesg
[ 1374.175812] glxinfo[10991]: segfault at 0 ip 0804ad46 sp bf9fe330 error 4 in glxinfo[8048000+5000]
[ 1640.623988] glxinfo[11679]: segfault at 0 ip 0804ad46 sp bf8fea30 error 4 in glxinfo[8048000+5000]
[ 1729.562879] glxinfo[12239]: segfault at 0 ip 0804ad46 sp bff11030 error 4 in glxinfo[8048000+5000]
[ 2075.227586] glxinfo[13118]: segfault at 0 ip 0804ad46 sp bfd51e70 error 4 in glxinfo[8048000+5000]
[ 2740.164832] glxinfo[15393]: segfault at 0 ip 0804ad46 sp bf850170 error 4 in glxinfo[8048000+5000]

I see that normally libglx.so is installed by xserver-xorg-core package like this 
/usr/lib/xorg/modules/extensions/libglx.so

but nvidia driver installation sets up an alternate libglx like this 
 lrwxrwxrwx 1 root root   19 2009-08-31 12:28 libglx.so -> libglx.so.185.18.36
-rwxr-xr-x 1 root root 1.3M 2009-08-31 12:28 libglx.so.185.18.36
in the same path /usr/lib/xorg/modules/extensions
also nvidia  driver replaces /usr/lib/libGL.so to its driver version of libGL.so like this 
 lrwxrwxrwx 1 root root       10 2009-08-31 12:28 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root       18 2009-08-31 12:28 libGL.so.1 -> libGL.so.185.18.36
-rwxr-xr-x 1 root root   618176 2009-08-31 12:28 libGL.so.185.18.36

same with libGLcore.so.1 also like this 

lrwxrwxrwx 1 root root       22 2009-08-31 12:28 libGLcore.so.1 -> libGLcore.so.185.18.36
-rwxr-xr-x 1 root root 16118572 2009-08-31 12:28 libGLcore.so.185.18.36

so whats wrong with glx extension ? does it mean incompatibility with libglx.so library from nvidia  ? could someone suggest a workaround ?

pls find the xorg.conf attached.
 
regards,
Krishnamo

---

### Post by L33tCh on 2011-01-07
Just thought I'd let you know we're working on the problem [here]("http://ubuntuforums.org/showthread.php?t=1660243"). I really REALLY want to sort it out, so hopefully when I'm done, that will be the link to the solution ;)

---

### Post by bodymind on 2012-01-14
check it out in here:

[http://askubuntu.com/questions/87149/intel-hd-3000-sandy-bridge-3d-games-problem/95441#95441](http://askubuntu.com/questions/87149/intel-hd-3000-sandy-bridge-3d-games-problem/95441#95441)

---


---
title: "OpenGL error when starting wolfenstein"
date: 2006-03-18
forum: General Help
---

### Post by maddog39 on 2006-03-18
Hello all,

I am starting to migrate completely to linux and so I have just installed my favorite game of all time, Woflenstein: Enemy-Territory. Now I get it all installed but when it starts up I get..
> 
------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Error couldn't open the X display
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Error couldn't open the X display
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsyst

I am using the Vesa driver because its the only thing that supports the nVidia 6100 chipsets.

Thanks!
-maddog39 :D

---

### Post by evilgold on 2006-03-18
VESA doest support direct rendering as far as i know. You cant use the offical nvidia drivers with that card?

---

### Post by Adramelech on 2006-03-19
This are the supported and not supported chipsets of drivers 

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

cant see 6100 :(

I got wolfenstein et running with this


[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by Barrakketh on 2006-03-19
[QUOTE=Adramelech]This are the supported and not supported chipsets of drivers 

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

cant see 6100 :([/QUOTE]
You're looking in the wrong place.  See this: [http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html)

The 6100 is listed :)

Grats on getting it fixed though.

---

### Post by maddog39 on 2006-03-21
Okay guys, I found a driver and I am trying to install but I get this error.
[IMG]http://images.dx-h.com/files/1/nvidia_error.png[/IMG]
I also tried doing an apt-get on the package; binutils but got an error with the sources list.

---


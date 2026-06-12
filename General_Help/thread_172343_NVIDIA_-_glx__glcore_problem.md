---
title: "NVIDIA - glx / glcore problem"
date: 2006-05-08
forum: General Help
---

### Post by sbakker on 2006-05-08
EDIT: Problem fixed.  After doing all the installs, I neglected to ctrl-alt-bckspc



I'm new to Ubuntu, and still a linux novice, but I've been trying to follow guides to install nwn.

When I try to run the game, I get the following error:

[INDENT]Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Failed to initialize graphics.[/INDENT]

My xorg.conf has the proper entries:

[INDENT]Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection[/INDENT]

and

[INDENT]Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
    Driver         "nvidia"
EndSection[/INDENT]

However, my Xorg.0.log shows this:

[INDENT](II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
[/INDENT]

Also, the output on glxinfo is this:

[INDENT]name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None[/INDENT]


I'm running Dapper and have a NVIDIA GeForce4 TI 4200 Video Card.  Anyone know what could be wrong and how to fix this?

---


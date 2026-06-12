---
title: "Latest NVidia driver problem"
date: 2006-06-02
forum: General Help
---

### Post by limaunion on 2006-06-02
Hi All! I'm having some problems while trying to start X with the nvidia driver (I'm  running latest vanilla kernel).

This is the error I'm getting:

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "3"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

I've the following in my xorg.conf: 
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

The modules are loaded correctly:
Module                  Size  Used by
nvidia               4544724  0
forcedeth              18308  0
nvidia_agp              5404  1
agpgart                22768  2 nvidia,nvidia_agp

What's wrong ? any ideas ?
Thanks in advance for any help.
JC

---

### Post by limaunion on 2006-06-02
well, I've already found a clue:

Jun  2 23:44:11 server kernel: [ 5653.232918] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
Jun  2 23:44:11 server kernel: [ 5653.482362] NVRM: API mismatch: the client has the version 1.0-8756, but
Jun  2 23:44:11 server kernel: [ 5653.482364] NVRM: this kernel module has the version 1.0-8762.  Please
Jun  2 23:44:11 server kernel: [ 5653.482366] NVRM: make sure that this kernel module and all NVIDIA driver
Jun  2 23:44:11 server kernel: [ 5653.482368] NVRM: components have the same version.

any ideas ? The driver installation finished properly.

---

### Post by limaunion on 2006-06-02
Well, I solved part of the problem by downgrading the driver to the previous release. Anyway I'm still having this problem: 

(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

and glxinfo's output:

name of display: :0.0
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
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

so?

---

### Post by alexnorman13 on 2006-06-03
Bottom of this forum link has the solution for that. Same problem happened to me and this worked.

[http://www.ubuntuforums.org/showthread.php?t=184303&page=5&highlight=nvidia+driver+mismatch](http://www.ubuntuforums.org/showthread.php?t=184303&page=5&highlight=nvidia+driver+mismatch)

---


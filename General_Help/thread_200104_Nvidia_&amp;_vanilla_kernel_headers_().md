---
title: "Nvidia &amp; vanilla kernel headers (?)"
date: 2006-06-19
forum: General Help
---

### Post by limaunion on 2006-06-19
Hi, I'm having some problems with the nvidia driver (8762), basically I'm getting this from xorg.log:

(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
...
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 440 with AGP8X at PCI:2:0:0

and with glxinfo I get:
$ glxinfo
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

So far I've not been able to find a solution yet, but found this tutorial [http://www.albertomilone.eu/europeo/latest_nvidia_udsf.html](http://www.albertomilone.eu/europeo/latest_nvidia_udsf.html) and I'm stuck on Method 2 step 8 where it says: 
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`

I'm running my own kernel and never had a problem with the nvidia drivers till I switched to Dapper. Currently I'm running vanilla 2.6.17 but don't have a  /usr/src/linux-headers directory, just have /usr/src/2.6.17 from where I made my own compilation. 

Does anyone know where should I find the kernel headers from a vanilla source ?
Any other suggestion in order to solve the problem reported ?

Thanks in advance.
Jorge.-

---

### Post by tseliot on 2006-06-20
> **limaunion]Hi, I'm having some problems with the nvidia driver (8762), basically I'm getting this from xorg.log:

(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
...
(EE) NVIDIA(0): Failed to initialize the GLX module said:**
> http://www.albertomilone.eu/europeo/latest_nvidia_udsf.html[/url] and I'm stuck on Method 2 step 8 where it says: 
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`

I'm running my own kernel and never had a problem with the nvidia drivers till I switched to Dapper. Currently I'm running vanilla 2.6.17 but don't have a  /usr/src/linux-headers directory, just have /usr/src/2.6.17 from where I made my own compilation. 

Does anyone know where should I find the kernel headers from a vanilla source ?
Any other suggestion in order to solve the problem reported ?

Thanks in advance.
Jorge.-
Pay more attention to my guide. Read Step 8 again and notice where it says "OTHERWISE if you are using a kernel which you compiled from vanilla sources (i.e. from kernel.org) then you have two options:"

And BTW you could use my script to automate all Method 2:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---


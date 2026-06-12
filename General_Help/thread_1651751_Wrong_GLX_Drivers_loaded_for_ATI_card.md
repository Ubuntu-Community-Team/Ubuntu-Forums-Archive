---
title: "Wrong GLX Drivers loaded for ATI card"
date: 2010-12-23
forum: General Help
---

### Post by mewashen on 2010-12-23
I am having a problem with the wrong GLX driver being loaded in Ubuntu Maverick. I have an old ATI card using the open source drivers.

Here is my Video card info:
lspci | grep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]

When I run glxinfo I get this:
glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".

In the Xorg.0.log file I noticed these entries:
[    28.692] (II) LoadModule: "glx"
[    28.692] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    31.484] (II) Module glx: vendor="NVIDIA Corporation"
[    31.484] 	compiled for 4.0.2, module version = 1.0.0
[    31.484] 	Module class: X.Org Server Extension
[    31.484] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 07:01:31 PDT 2010
[    31.484] (II) Loading extension GLX

later in the Xorg.0.log file:
[    32.024] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

If I rename the libglx.so file to .old then another driver gets loaded but glxinfo will now respond but still gives an error mentioning NV.

Does anyone know how to get the proper drivers loaded?

---

### Post by Jiyuuma on 2011-01-31
I had the same problem. I checked which nvidia drivers I had installed with "sudo aptitude search nvidia", which showed that I had the nvidia-96 drivers installed, along with some other nvidia packages, so I executed the following;

sudo apt-get --purge remove nvidia-96 nvidia-96-modaliases nvidia-common nvidia-current-modaliases nvidia-settings

Then after restarting gdm the radeon GLX drivers loaded successfully.

---

### Post by Mark Phelps on 2011-01-31
In Maverick, since you are using the open source drivers, you don't need an Xorg config file.  So, go into a terminal, and as root, rename the config file to something else.  Reboot.

When you restart, you should get working video.

---

### Post by mewashen on 2011-03-05
Thank-you Jiyuuma. This has solved my problem. THe proper GLX drivers are now being loaded.

---


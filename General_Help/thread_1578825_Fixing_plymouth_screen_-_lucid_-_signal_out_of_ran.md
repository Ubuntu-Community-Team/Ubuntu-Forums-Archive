---
title: "Fixing plymouth screen - lucid - signal out of range"
date: 2010-09-21
forum: General Help
---

### Post by Chethan S on 2010-09-21
I followed the instructions given at [http://linuxhub.net/2010/06/fix-big-and-ugly-plymouth-in-ubuntu-10-04-lucid-lynx/ ]("http://linuxhub.net/2010/06/fix-big-and-ugly-plymouth-in-ubuntu-10-04-lucid-lynx/")for fixing my ugly plymouth screen after installing Nvidia drivers. All worked as expected. However I made some modifications in the instructions as I required.

They were,

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap

```

I used 1366*768 instead of 1280*1024. 

I didn't replace ```
GRUB_GFXMODE=640x480
``` with ```
GRUB_GFXMODE=1280x1024
``` as it would be hard to visualize in the grub screen. 

Now my problem is I am able to see the nice plymouth but the monitor displays an error as 

[CENTER]Input signal out of range, so set 1366*768 and 60 Hz. 
[/CENTER]

Can't make out what is the problem now.

---

### Post by tomgibson on 2010-09-24
I have this same problem, only my monitor displays nothing except an out of range notice, I assume the problem is the refresh rate, how can this be specified explicitly in the grub commands in the original article?

EDIT: Just to clarify, before installing the NVidia drivers I get the Plymouth screen at 1440x900 (native resolution of my screen) but after installing the drivers it defaults to a low resolution. Using the above fix and specifying 1440x900 means I don't see the screen only an out of range error on monitor.

---

### Post by Chethan S on 2010-09-24
> before installing the NVidia drivers I get the Plymouth screen at  1440x900 (native resolution of my screen) but after installing the  drivers it defaults to a low resolution. Using the above fix and  specifying 1440x900 means I don't see the screen only an out of range  error on monitor.Same was the problem I faced. Before installing nvidia drivers the monitor could display 1366x768 but after installing Nvidia drivers it defaulted to 640x480 resulting in ubuntu being displayed twice in the same screen, that too not clearly. 

Later I decreased my resolution to 1280x720 instead of 1366x768. Then everything works fine. No error message. But if you change the resolution in GRUB_GFXMODE also, if you are dual-booting then it would be really hard to see the OS choices.

Therefore I suggest you to set the resolution to a slightly lower one than 1440x900 at
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
and proceed with the steps given in the blog article.

---

### Post by tomgibson on 2010-09-26
This is the workaround I settled on eventually, although it is still not ideal as before Plymouth worked with my screen's native resolution, whereas now it is at a reduced but better than 640x480 resolution.

Having done a bit more digging I think this is the best I am going to get, since it would appear that Plymouth requires some particular driver feature which is not implemented in the Nvidia non-free drivers, but is present in nouveau. Unless Nvidia implements this feature (which I gather from other forum posts is unlikely) I do not see any proper solution except this slightly reduced resolution workaround. Perhaps when I get a new more capable screen at some point it will no longer be an issue, but that isn't likely to happen any time soon!

Thanks anyway.

---


---
title: "nvidia problem, no screens found"
date: 2009-08-23
forum: General Help
---

### Post by tombaugh on 2009-08-23
Hi,

I recently upgraded to Ubuntu 9.10, because I had a problem with my printer, which supposedly would be fixed in the latest release. Because the fan of my graphics card was spinning at max speed after the upgrade, I decided to reinstall the nvidia drivers. The result was that the system hanged during boot, so I booted in recovery mode and removed the driver. I installed nvidia-glx but I cannot start X. This is what the log says:

> ...
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found

lspci

> 01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

xorg.conf
> 
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "NoLogo" "True"
Driver "nvidia"
EndSection Many thanks in advance

---

### Post by tombaugh on 2009-08-23
solved by installing the driver from the nvidia website

---


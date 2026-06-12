---
title: "Black screen no matter which Nvidia driver I use"
date: 2010-07-17
forum: General Help
---

### Post by Boris and Bailey on 2010-07-17
I inherited a Dell Dimension e521 which comes with onboard Nvidia graphics (Nvidia integrated video [DirectX 9.0 Shader Model 3.0 Graphics Processing Unit) and a Nvidia GeForce 6150LE chipset. I erased the drive and put Ubuntu 9.04 on. I upgraded the BIOS so the cursor wouldn't stick. Only one problem left: I cannot find a Nvidia driver that will work so that I can increase the screen resolution from 800x600. I've tried them all from the earliest to latest version.

Every Nvidia driver I have tried results in a black screen after booting. Even the installation of Ubuntu 10, which has its own open-source Nvidia driver, results in the usual message that a higher resolution should be used followed by a black screen. Back to Ubuntu 9.04 so I can see the desktop.

Is there anything I can do to get a higher resolution?

---

### Post by dino99 on 2010-07-17
remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf  ( drived by kernel now)

with synaptic:

jockey-gtk need to be installed
nvidia-glx-185 is your driver

reboot without "splash" (edit boot line)

then check driver activation: system admin hardware driver, nvidia-current should be activated

---


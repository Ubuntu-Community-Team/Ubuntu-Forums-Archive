---
title: "Screen Resolution problems"
date: 2006-04-09
forum: General Help
---

### Post by datim on 2006-04-09
Hi,

I have a Ubuntu 5.10 machine that dual boots with Windows XP running an NVIDIA GeForce 4 MX440.

I never usually go into Windows on this machine, but decidied to tonight when I did, the next time I went into Ubuntu, the screen resolution is 640x480 and I can't change it. I am running the latest NVIDIA drivers installed via Automatix, I tried editing xorg.conf to change the provider to nv (ie inbuilt nvidia drivers) and it made no differnence.

Help please!

Thanks,
David

---

### Post by slipk487 on 2006-04-09
run 
```
sudo dpkg-reconfigure xserver-xorg
```
and reselect the screen resolutions

---

### Post by tseliot on 2006-04-09
Or follow this guide:
[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

---


---
title: "NVIDIA problem"
date: 2011-01-21
forum: General Help
---

### Post by j.barker on 2011-01-21
I'm running Ubuntu 10.10 with an NVIDIA GeForce 6100 video adapter and my monitor seems to flicker whenever the the computer is processing. My system is up to date and I did install the recommended NVIDIA driver. The monitor isn't going blank or anything like that, it just seems like every once in a while different images will pop up for less than a second. Any ideas as to what the problem might be? I've attached a copy of the xorg.conf file as well:


Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Default Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

---

### Post by yetiman64 on 2011-01-22
Sometimes the NVIDIA driver and compiz will clash. If you are also suffering with video tearing during playback (I'm not sure from your question if you are), you could check out the link below and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1390284](http://ubuntuforums.org/showthread.php?t=1390284)

This link helped me get rid of some effects/artifacts etc with an NVIDIA GT240 card in use on Lucid. Good Luck.

---


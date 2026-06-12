---
title: "Black screen after installation"
date: 2012-03-08
forum: General Help
---

### Post by krayzie906 on 2012-03-08
Hi there! From what I understand, this is a quite common problem, but I couldn't fix it.

I tried this with all the Ubuntu versions from 10.04.4 to 11.10 and got the same results.
After a fresh Ubuntu install, I restart computer when asked. Upon startup the screen either goes black or messed up (white with some black symbols), and keyboard freezes. Monitor shows "Special mode 60something kHz / 70 Hz"

CPU: AMD Sempron 2500+
GPU: Nvidia GeForce FX 5500

I can boot using recovery mode and failsafex, but there's no option in recovery mode in Ubuntu 11.10 (that I'm currently on).
Tried installing nvidia drivers both using "Additional drivers" and following instructions on nvidia homepage.
Tried removing and reconfiguring xorg.conf
Tried restarting xserver.
Tried adding "nomodeset" in grub.
Nothing helped, and I'm concerned, that problem could be in my hardware, although it can run Windows XP and 7

xorg.conf file on fresh install:
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by Ni-el on 2012-03-08
I would guess at the  Nvidia GeForce card. That sounds like an old series.
You may find a suitable driver through synaptic. Or if you have the windows cd that came with the card, you may be able to install using ndiswrapper

---

### Post by krayzie906 on 2012-03-08
I do have a CD for windows. Could you explain the ndiswrapper part? (Complete noob here :) )

---

### Post by winh8r on 2012-03-08
Have you looked at this guide?


[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Hope this helps

---

### Post by krayzie906 on 2012-03-08
Yes, and it didn't help :(

I'm going to try installing Ubuntu 12.04 now. If I'm not back in 30 mins, my computer died.

---

### Post by krayzie906 on 2012-03-08
I am an idiot. My processor is AMD 64-bit, but I was trying to install i386 version of Ubuntu. Problem solved :)

---

### Post by haresear on 2012-03-08
Really? I didn't know that would cause a problem. I've installed and used i386 OS versions on my 64-bit desktop machine with no issues (don't have an Nvidia card tho).

---


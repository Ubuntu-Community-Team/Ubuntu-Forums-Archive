---
title: "Need help to Optimize the Nvidia private drivers and remove the lag effect"
date: 2010-11-21
forum: General Help
---

### Post by Vegaxus on 2010-11-21
Hi everyone.

After having tried to fix the plymouth without any successfully result (i am meanning the thread i began few weeks ago and sited here: [http://guide.ubuntuforums.org/showthread.php?t=1610122](http://guide.ubuntuforums.org/showthread.php?t=1610122)). I decided to keep nvidia's privates drives on giving up any hope to fix the plymouth bug and, right now, i would like to optimize or configurate the drivers properly like it is on Mandriva One 2010.

Perhaps someone is not exactly understand what i want to say. Well, i was using Mandriva One 2010 before installing Ubuntu Maverick and i have noticed there was no a low latency, lag effect, low performance or a lack of initial smooth and clean windows moves in Mandriva One 2010 but on Ubuntu there is. 

This is very hard to explain for me, for example, If i use the "flip windows selector" (i mean, pressing "<Super>+Tab" keys) show me this effect too slow initially but if i forced the GPU for a while (repeating and pressing the keys), the lag effects vanished and then, the flip windows selector works nicely fast, clean and smooth. Now if i stop to use that effects, let the Nvidia GPU repose a while and use again the flip windows selector again, the lag effects come up again.

This fact does not just happen using the "flip windows selectos", any effects which minimize, resize or maxime the windows generate that annoying initial lag effects, for example, a simple minimize windows:

[IMG]http://img63.imageshack.us/img63/4440/lagv.png[/IMG]

I am in despair with this, i do not if i have to do some change in the /etc/X11/xorg.conf file, what i have to configurate in the "Nvidia X server Settings" or in the "compiz manager settings" application.

Anyone knows a tutorial about how to optimize the Nvidia drivers on Ubuntu? or the Compiz effects to reduce the lag effets?

---

### Post by white_hat on 2010-12-10
in xorg.conf


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
    Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"

EndSection
```

---


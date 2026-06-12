---
title: "Kubuntu Splash Corruption on Shutdown"
date: 2006-06-10
forum: General Help
---

### Post by CrypticBlade on 2006-06-10
Running 6.06 Kubuntu.

When shutting down my laptop the Kubuntu splash logo appears distorted and discolored. I also notice that it takes several seconds for the shutdown splash screen to appear. I actually have time to see some of the messages about daemons being stopped before the Kubuntu splash ever shows up.

As I said previously, when it finaly does show up, it is distorted and discolored. The boot splash is fine on startup, just having this problem on shutdown.

Pretty strange... :confused:

---

### Post by CrypticBlade on 2006-06-11
RESOLVED:

I installed nvidia-glx package and edited the xorg.conf file to change the video driver from "nv" to "nvidia". Rebooted and my corrupted shutdown splash screen was fixed. This also fixed some flickering of the display and as an added bonus gave me Direct Rendering support for 3D applications! :)

---


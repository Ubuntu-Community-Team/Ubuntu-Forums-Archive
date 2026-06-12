---
title: "(Karmic) nVidia driver issues. :("
date: 2009-12-18
forum: General Help
---

### Post by fark0 on 2009-12-18
Hello wise sages,

I am running Ubuntu 9.10 Karmic with a geForce 7350LE (which is on the supported list). I installed the recommended proprietary nVidia driver using the 'Hardware Drivers' GUI (version 185). On boot, X fails and throws me to a text-mode login, and the screen flashes vertically as if the VYSNC was off or something. The keyboard entry is also spotty, forcing me to reboot into recovery mode, remove /etc/X11/xorg.conf, and startx / reboot to get X to work again. 

One thing that I feel like I should mention is that the geForce 7350LE only uses DVI, as does my monitor. I wouldn't think this would be an issue, but who knows.

Here are some logs, provided for your viewing pleasure.

/var/log/Xorg.0.log: [http://pastebin.com/m2b35c1a1](http://pastebin.com/m2b35c1a1)
/etc/X11/xorg.conf (generated with nvidia-xconfig): [http://pastebin.com/m50d92319](http://pastebin.com/m50d92319)

Thank you. :)

---

### Post by fark0 on 2009-12-18
bump :(

---


---
title: "CPU freq scaling! No wai!"
date: 2009-11-17
forum: General Help
---

### Post by Jungle-Cat on 2009-11-17
Hey all,
Something is scaling my CPU freq from 3.1 to 2.07GHz. I just disabled SpeedStep in the BIOS (Abit IP35-Pro, E4300), but both cat /proc/cpuinfo and the Gnome bar applet say it's at 2.07GHz, but under load it does go up to 3.1GHz suggesting that the applet is working right. I installed Bootup-Manager (BUM), disabled all the power-saving orientated services but it's still sitting there at 2.07.

Does anyone know what's scaling it?

Thanks

---

### Post by nixed242 on 2009-11-17
Just a guess, but you could try disabling the S99ondemand script in your /etc/rc5.d directory.

[http://embraceubuntu.com/2005/09/09/removing-or-editing-a-startup-script/](http://embraceubuntu.com/2005/09/09/removing-or-editing-a-startup-script/)

---

### Post by Jungle-Cat on 2009-11-17
I did some more searching, did some things and installed some freq utils package of some sort... the applet now lets me select what profile and frequency to use.

Thanks, though!

---


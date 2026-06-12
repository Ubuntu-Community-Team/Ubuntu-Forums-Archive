---
title: "ubuntu 10.04 bluetooth mouse scroll wheel not working"
date: 2010-05-27
forum: General Help
---

### Post by dpc.ucore.info on 2010-05-27
Hi,

I'm working with Ubuntu 10.04 x64 + Asus 1201N + Media-Tech MD1083 RELOADED bluetooth mouse. Gnome Bluetooth Applet has setup mouse perfectly except scrolling. Even back&forward buttons seem to work fine but the scroll wheel does not work at all.

In "xev" I can see that scrolling does not produce any events.

Can you please advise on the next steps? :)

---

### Post by dpc.ucore.info on 2010-06-02
I'm trying to add custom mouse config to xorg.conf.d / xorg.conf but I now see that mouse is different device under /dev/input/mouseX each time I log in. And I'm not sure what to set there. :/

---

### Post by SunnyBUG on 2010-06-26
Same problem for me with BTC Bluetooth mouse.
Mouse wheel is not producing any events at all.
Tried both "xev" and "cat /dev/input/eventXX"

All other buttons produce events. Except the mouse wheel.

---


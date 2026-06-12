---
title: "Wine Stay in &quot;Windowed Mode&quot;"
date: 2012-03-27
forum: General Help
---

### Post by CrusaderAD on 2012-03-27
Is there a way to make wine programs stay in a "windowed" mode that I can move around my desktop? I know you can "emulate" a virtual desktop, but it always sticks it into one corner of my screen and I can't move it.

---

### Post by GaryMac on 2012-03-27
I'm using Ubuntu 10.04 and I have certain games installed ..
They open in a window which can be moved.
 
Launcher env WINEPREFIX="/home/account/.wine" wine "C:\Program Files\xxxxx\xxxxx\xx.exe" -windowed -w 1024 -h 768
 
In Wine config ...  add application & set Graphic Tab to emulate virtual desktop ..
with same width & height as in launcher.

---


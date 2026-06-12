---
title: "Problems with ATI X700 Pro"
date: 2006-02-21
forum: General Help
---

### Post by tig4 on 2006-02-21
I currently have an ATI X700 Pro installed on a 64 bit AMD chip. I installed the 32 bit Ubuntu (Which shouldnt matter) and when I try to start it, it crashes when trying to startup X Server. Says cannot start x-server.

Any ideas?
Tig

---

### Post by RAOF on 2006-02-22
Yup.  The default (open source) drivers for your ATI card don't work with new(ish) cards like yours.  (I'm not quite sure why they're still the default :rolleyes: ).  As a temporary solution, you can get a GUI by loging in at the terminal (Press Ctrl-Alt-F1 when it says "failed to load x-server") and the running "sudo dpkg-reconfigure xserver-xorg".  It'll ask a whole bunch of questions; the defaults are fine (unless you know better).  It will also give a list of graphics drivers - ati, nv, trident, etc.  From that list, select "vesa" (a fail-safe driver).  Once you're done, type "sudo /etc/init.d/gdm restart" to start your GUI.

For a faster, better, stronger fix, you can then follow the "ATI Drivers" link in my sig :)

---


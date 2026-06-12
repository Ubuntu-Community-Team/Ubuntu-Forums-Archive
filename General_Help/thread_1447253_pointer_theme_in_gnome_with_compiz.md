---
title: "pointer theme in gnome with compiz"
date: 2010-04-05
forum: General Help
---

### Post by adpads on 2010-04-05
I'm running a fresh reinstall of ubuntu karmic which is loading its settings from an old /home partition.

For some reason, gnome (with compiz/emerald) is starting up with the wrong pointer theme. I have set it to use DMZ, but it is starting up with oxy-black. When I issue "compiz --replace" this is corrected, but I can't get it to stick, no matter how many times I go into system>preferences>appearance>theme>customise>pointer and set it.

Could this have something to do with the fact that I am having to use the old-fashioned way to load compiz, by adding "compiz --replace" to the startup applications?

Thanks to all!

---

### Post by adpads on 2010-04-05
Update: While I have a sense that something is more deeply wrong, I did find this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647)

The workarounds described there, specifically, editing /usr/share/icons/default/index.theme, and gconf-editor > desktop > gnome > peripherals > mouse > cursor_theme, did allow me to set a consistent theme - but something is still fishy about startup on my system and I suspect a conflict somewhere.

---

### Post by draki on 2010-04-13
I have the same problem and have tried the same workarounds to no avail :-(

I'm on Lucid Beta 2 64bit

Any suggestions on how to fix?

---

### Post by adpads on 2010-04-14
Like I say, the trick that worked to me was to paste in my own /usr/share/icons/default/index.theme. I used exactly the contents in that thread I linked to above. I would paste it in again but am on a Fedora installation now - which, incidentally, has the same problem, and a somewhat different-looking /usr/share/icons/default/index.theme..

---


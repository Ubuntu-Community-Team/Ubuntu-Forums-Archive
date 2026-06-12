---
title: "Ubuntu tty1-6 just showing tiny gnome desktop"
date: 2010-09-06
forum: General Help
---

### Post by makaveli789 on 2010-09-06
I am on a brand new install of Win7 Pro x64 and I have VirtualBox installed with Ubuntu 10.04 running as a guest OS. I want to get access to the tty1 so I press CTRL + ALT + F1. The screen resizes to a smaller size, turns black, then the gnome desktop reappears but only the top left corner.

Any ideas what could be going on?

---

### Post by makaveli789 on 2010-09-06
Just tried uncommenting the following line in /etc/default/grub:
[COLOR=#008080][I]#GRUB_GFXMODE=640x480

[/I][/COLOR]And then ran sudo update-grub2, followed by a reboot. Same result.

---

### Post by makaveli789 on 2010-09-06
Well it seems if I turn off Compiz effects then it works ok. I would like to use Compiz though. Has anyone experienced problems with this in the past and possibly solved it?

---

### Post by makaveli789 on 2010-09-06
Any thoughts?

---

### Post by makaveli789 on 2010-09-08
Apparently this is a known issue with VirtualBox and Compiz.

---


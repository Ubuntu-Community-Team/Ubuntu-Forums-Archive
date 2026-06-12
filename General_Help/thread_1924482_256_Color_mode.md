---
title: "256 Color mode?"
date: 2012-02-12
forum: General Help
---

### Post by brpylko on 2012-02-12
I am running ubuntu 11.10 off of a flash drive, and, to increase performance, want to set the color mode to 256 colors. Googling has yielded no results, and I cannot figure out how to do this.

---

### Post by JC Cheloven on 2012-02-12
I'm afraid I can't be very precise, but as far as I remember, it could be done editing /etc/X11/xorg.conf

Now this file is somehow deprecated in ubuntu, and it doesn't exist by default. You'll have to generate it from a console (ctrl-alt-F1), stopping the desktop manager first (sudo service gdm stop), running "sudo Xorg -configure" and then adding "DefaultDepth ??" to the monitor 0 section (where ?? is a number I can't remember, perhaps 8, which will indicate how many colors will be used).

Please take the above only as a start point for your own findings, as I don't remember really the exact procedure. Hope it helps.

---


---
title: "Pink Screen (No Text) after GRUB Boot in Graphics Mode"
date: 2011-07-31
forum: General Help
---

### Post by wfunction on 2011-07-31
On Ubuntu 11.04 x64, when I select an operating system in GRUB, I don't get the system output log that is normally there. Instead, I get a nice, pink screen that only goes away when the system goes into full graphics mode.

If I use GRUB_TERMINAL=console then it WILL display the information I want, but in low-resolution *text* mode. I want it to be displaying that information at *full* resolution (i.e. 1600x900) on my laptop; how do I do this?

Right now I have

GRUB_GFXMODE=1600x900

in /etc/default/grub (and yes, I've obviously run update-grub).

(This **worked fine** on 10.04.)

---


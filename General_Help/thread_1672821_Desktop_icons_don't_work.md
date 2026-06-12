---
title: "Desktop icons don't work"
date: 2011-01-21
forum: General Help
---

### Post by dg14813 on 2011-01-21
Our class is working on Ubuntu for this unit.  Our lab computers are old unbranded computers running old Intel Pentium III's with 512MB of RAM.

We've had a few issues with it running on the old hardware, first the gnome panels wouldn't show up, but that was fixed with the killall gnome-panels command.  Then if we log out then try to log back in it will keep logging us out, and now anything that's on the desktop will not show up, the right-click menu doesn't work either.

---

### Post by tredegar on 2011-01-21
Running out of disk space can cause this.

CTRL-ALT-F2
You should get a terminal login.
Login to the terminal as yourself and look at the output of **df -h**
Anything showing over 90% "in use" means trouble ahead, as 5% is normally reserved for root's use only.
**sudo shutdown -h now** to turn the PC off from the terminal.

But your RAM at 512MB is very tight for gnome. It would help a lot if you could double it. Old chips are cheap second-hand. Meanwhile, I hope you have swap space enabled.

You might be better off running a lighter distro ( puppy ? ) and / or a lighter window manager ( xfce ? )

Good luck.

---


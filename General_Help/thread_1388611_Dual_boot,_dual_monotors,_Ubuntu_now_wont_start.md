---
title: "Dual boot, dual monotors, Ubuntu now wont start"
date: 2010-01-23
forum: General Help
---

### Post by Ottis on 2010-01-23
Dell Optiplex 210L
Windows XP home
Ubuntu 8.04
Primary monitor; on board graphics
Secondary monitor; ATI PCI card

I recently installed an ATI PCI graphics card to run a 2nd monitor,  now whenever I boot the grub menu shows up on the 2nd monitor and Ubuntu tries to start on the 2nd monitor but never gets to the login screen.
Everything works fine with XP.
The only way I can boot to Ubuntu is to pull out the PCI card before turning on my PC.
I know that Ubuntu doesn't do dual monitors without a LOT of work, (or at least a lot for a n00b like me) so is there some way to make grub and Ubuntu ignore the ATI card and just use the on board graphics?

If all else failes, I'll just forget about the 2nd monitor, while it's handy for some of the stuff I do it's not 100% nessary.

Thanks,  Otis

---

### Post by Ottis on 2010-01-23
Bump.
*Is* there a way to make Grub and Ubuntu use the on board graphics and ignore the PCI card????
At this point I'm not interested in getting both monitors to work with Ubuntu, just the one.
**********************

**Edit;**
I found a setting in the BIOS that I had previously overlooked, that fixed the problem.

---


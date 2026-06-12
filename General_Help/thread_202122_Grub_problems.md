---
title: "Grub problems"
date: 2006-06-22
forum: General Help
---

### Post by nation on 2006-06-22
I've got a Breezy Badger box set up for MythTV, and I want to be able to have the computer start up on alarm to record shows when I'm not home.  I can set the alarm OK in my BIOS, but it needs a restart and immediate shutdown to work right.

I've been trying to follow instructions here: [http://www.mythtv.org/wiki/index.php/Shutdown_Wakeup](http://www.mythtv.org/wiki/index.php/Shutdown_Wakeup)

but there's a bunch of modifications for new versions and such.  More importantly, grub-set-default isn't on my system.  That sounds like the easiest option, but it's just not there.  I found a page or two claiming that it's not in the Debian package for whatever reason.  I've also tried the 
echo "savedefault --default=3 --once quit" | grub
line and that doesn't work either.  ( The immediate shutdown is the fourth option, so the number is 3).

In fact, I set up the menu.lst file to savedefault 3 when booting normally, so that it would reboot into the immediate shutdown after a normal start, and it still started normally (and yes, I have the line "default  saved" in the menu.lst file).  I'm at a loss right now as to where to look.  Any ideas?

---


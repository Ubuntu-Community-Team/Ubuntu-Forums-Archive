---
title: "Ubuntu 9.10 gets crazy after changing panel position"
date: 2009-10-24
forum: General Help
---

### Post by yabune on 2009-10-24
Hi,

I had a panel in the bottom of the screen, and I just move the top panel also to the bottom and define it with auto-hide.

After that I wasn't able anymore to use both panels.
They stay in the background consuming cpu and don't respond, so I can't do anything now. I tried to open the run (ALT F2) but nothing happens. I can only press the power button and shutdown the computer.

I tried to enter in recover mode, but it crashes.

How can I recover the initial state?

Any help is apreciated!!!

Thanks!

---

### Post by mikewhatever on 2009-10-24
The recovery mode crashing is odd and shouldn't be related because no GUI is loaded at all. Perhaps there are other problems, but let's deal with panels first. To restore the original settings, you'll need to delete everything in .gconf/apps/panel which is located in your home folder. Try booting from the live cd, then browse to the Ubuntu partition and your home folder. Once there, press ctrl+h to make hidden folders visible.

---

### Post by yabune on 2009-10-25
> **mikewhatever said:**
> The recovery mode crashing is odd and shouldn't be related because no GUI is loaded at all. Perhaps there are other problems, but let's deal with panels first. To restore the original settings, you'll need to delete everything in .gconf/apps/panel which is located in your home folder. Try booting from the live cd, then browse to the Ubuntu partition and your home folder. Once there, press ctrl+h to make hidden folders visible.

ok, it worked! :)

Thanks a lot!

---

### Post by rpachecoh on 2009-12-01
Uff, I had exactly the same problem. Just five minutes using Linux once I decided not to use MS anymore and I find that problem. Now it's solved, keep on trying ;)

---


---
title: "Time is wrong after installing Ubuntu Inside Windows"
date: 2010-08-24
forum: General Help
---

### Post by ChaosChris2009 on 2010-08-24
After I installed Ubuntu inside Windows last night and rebooted to finish the installation, I finished the Ubuntu install

I booted back into Windows 7 and my time was wrong

I had to resync the clock on Windows 7

but why did Ubuntu change the time in Windows 7?

---

### Post by pricetech on 2010-08-24
Probably a different time zone setting in Ubuntu.  Could also be the fact that Ubuntu, like many other OSes, references local time according to GMT.  If it didn't get chance to reset the clock after install, then the clock could be off.

I've run into that before, even on windows boxen.  Just make sure the time zone is correct in both OSes and you shouldn't have any more problems.

---


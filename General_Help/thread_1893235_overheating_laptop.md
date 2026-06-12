---
title: "overheating laptop?"
date: 2011-12-09
forum: General Help
---

### Post by princeofnam on 2011-12-09
I have a HP g7-1070us and I've noticed that it will from time to time overheat and have the fan run haywire.  Conky used to display reasonable temperatures but recently it seems set at 7-8 degrees no matter how hot the laptop actually is.  I'm not exactly sure what's causing this.

---

### Post by bluexrider on 2011-12-09
Conky get its info from LM Sensors, a software that reports from BIOS info however I cannot tell you how reliable it truly is. 

Most computer motherboards have built in sensors. I would boot into the BIOS and check the "REAL" readings and possibly compare them to the Conky output.

---

### Post by princeofnam on 2011-12-09
Why does my laptop intermittently begin to overheat?  I have to reboot to stop it from happening?

---

### Post by bluexrider on 2011-12-10
> **princeofnam said:**
> Why does my laptop intermittently begin to overheat?  I have to reboot to stop it from happening?
i'm sure you probably heard of the kernel issues by now, did this start after upgrading and if so have you read the bug reports on how to fix it?

the other thing is to install Jupiter power management [http://sourceforge.net/projects/jupiter/files/](http://sourceforge.net/projects/jupiter/files/)

this may help control the fan and maintain power issues

BTW rebooting a hot computer is not really a good idea. It loads the already HOT CPU. Better to let it cool down some before rebooting. imho

---


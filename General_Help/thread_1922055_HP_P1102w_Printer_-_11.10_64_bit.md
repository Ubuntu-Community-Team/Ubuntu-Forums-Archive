---
title: "HP P1102w Printer - 11.10 64 bit?"
date: 2012-02-07
forum: General Help
---

### Post by gr8 on 2012-02-07
Will the HP LaserJet Pro P1102w Printer work with 64 bit Ubuntu 11.10? Can anybody confirm or deny before I purchase it?

---

### Post by wolfen69 on 2012-02-08
Googling for *HP LaserJet Pro P1102w linux* revealed that it is supported.

---

### Post by gr8 on 2012-02-08
Thanks for the help, but I would specifically like to know if it will run on 64 bit Ubuntu 11.10. There are many people who have successfully loaded this onto Ubuntu but there is no mention of whether it is 32 bit or 64 bit. I've run many things successfully on 32 bit which do not work under 64 bit.

Can anybody confirm this printer works for 64 bit Ubuntu 11.10?

---

### Post by ep_ on 2012-03-10
I'm 64 bit Kubuntu 11.10 My HP LaserJet Pll02w (USB wire connected) quit working several weeks back, perhaps after the upgrade from Natty or a recent CUPS upgrade.  Per the HP Device Manager:  Status is "Device communication error"  Code 5012.

I've searched for solutions, found others have similar problems o on various models, but have yet to fix the issue in my particular case.  Any help here?

---

### Post by ep_ on 2012-03-11
This issue has been solved by disabling the "smart install" feature on the printer. If enabled, the device will be detected as a CDROM so as to assist Windows users with the install process.

This bug and a work-around fix was pointed out by Sanjay Kumar.

[https://bugs.launchpad.net/hplip/+bug/951763]("https://bugs.launchpad.net/hplip/+bug/951763")

---


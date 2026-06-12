---
title: "Reinstalled Ubuntu due to screwup, now there's 2 of them!"
date: 2010-07-30
forum: General Help
---

### Post by kuraykillua on 2010-07-30
So I'm new to Ubuntu, and I've learned a lot in the last few days, and screwed up a lot too. Now that I'm more familiar, I decided to reinstall and start fresh. Now I have a new problem... despite formatting and reinstalling, the Grub screen now has 4 Ubuntu options (2 regular, 2 recovery) Is there any way I can remove some of them from the Grub menu? Oh, and I'm running dual boot as well, so Windows is also on this computer.

---

### Post by Skrynesaver on 2010-07-30
Screwing up is part of learning, don't get discouraged ;)

The list of boot options in grub, (and their boot order) is defined in ```
/boot/grub/grub.cfg
``` This file should not be manually edited instead use [Startup Manager]("https://help.ubuntu.com/community/StartUpManager")

---

### Post by kuraykillua on 2010-07-30
The startup manager doesn't have an option to delete any boot options...

---

### Post by worksofcraft on 2010-07-30
Whenever Ubuntu upgrades the kernel it leaves the old one there for you to boot, just in case there is a problem with the new one.

Once you are happy that it all works you can get rid of the old ones using System->Administration->Computer Janitor

After that you will have to update the boot menu which is done automatically with the command

sudo update-grub

---

### Post by kuraykillua on 2010-07-30
Hm. the Computer Janitor actually found nothing that needs cleaning.
However I had Ubuntu Tweak installed and I ran that. It found the older Kernels and I just checked all of them to be cleaned. I restarted my computer, and Wala! Problem solved. Thanks a bunch to everyone!

---


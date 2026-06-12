---
title: "GRUB troubles with dual boot"
date: 2009-11-18
forum: General Help
---

### Post by carl801 on 2009-11-18
Hi all!

I'm having trouble getting GRUB to recognize the Windows XP installation.  Running 9.10, GRUB recognized XP, no problem.  Life was fine till I upgraded to GRUB2.  GRUB2 never recognized XP.  I followed all the instructions in the Help pages ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)).  No joy.  I even tried re-installing XP, then rerunning GRUB2 grub-update.  No joy.

So, I decided to uninstall GRUB2.  I followed the directions on the help page (link above) for uninstalling GRUB2 (Beta 1.97) and reinstalling GRUB 0.97.  It looks fine, menu.lst shows the XP installation, but when I reboot, GRUB2 seems to be still running.  The GRUB menu says Beta 1.97, the menu is clearly from GRUB2, and XP does not show up.

So, what am I doing wrong?  

If I didn't need XP for Audible.com files (they still don't support Linux and I can't get Audible Manager to play Audible .aa files using Wine) I would bag XP altogether!

Thanks for any help!
Carl

---

### Post by ArinSky on 2009-11-18
you could just open your grub2 file and add xp in manually, kinda like how you have to do to windows 7 if you have grub1. I'm still learning grub2, maybe someone more experienced with it can tell you what to add into your grub2 file.

---

### Post by drs305 on 2009-11-18
After you removed G2 and reinstalled grub, did you run the "grub-install /dev/sdX"? It sounds like G2 may still be in the MBR.

You can generate a valid menu.lst and still have G2 on your system until your reinstall grub. You install grub, but you still have to run "sudo grub-install sdX".

---

### Post by carl801 on 2009-11-18
> **drs305 said:**
> After you removed G2 and reinstalled grub, did you run the "grub-install /dev/sdX"? It sounds like G2 may still be in the MBR.

You can generate a valid menu.lst and still have G2 on your system until your reinstall grub. You install grub, but you still have to run "sudo grub-install sdX".

drs305

That was it!  I thought I had done the reinstall, but obviously I hadn't!  

Thanks for your help!

Carl

---


---
title: "Windows over linux"
date: 2010-12-10
forum: General Help
---

### Post by hissou86 on 2010-12-10
hi
i have installed ubuntu in my pc. for test purposes (i am ubuntu beginner), i tried to fromat my pc through the way of installing directly xp (without uninstalling ubuntu before), but the problem was that when  xp installer rebooted my pc to complete installation, the reboot didn't take place.

thanks for help in advance

---

### Post by sikander3786 on 2010-12-10
> when xp installer rebooted my pc to complete installation, the reboot didn't take place.

Can you please explain what happened then? Was there any error message like "no operating system" or something like that after the Bios screen. Or what?

Once you delete the Ubuntu partitions from Windows installer, Ubuntu is no longer involved in any activities further ;-)

---

### Post by amedac on 2010-12-10
You didn't provide much details, but i can try to help. Boot ubuntu from live cd, then open Gparted (System -> Administration -> Gparted) and delete all linux partitions. That should solve the problem with installing windows.

I suggest for the future install OS for experimental purposes in virtual machine. :)

---

### Post by hissou86 on 2010-12-10
> **sikander3786 said:**
> Can you please explain what happened then? Was there any error message like "no operating system" or something like that after the Bios screen. Or what?

Once you delete the Ubuntu partitions from Windows installer, Ubuntu is no longer involved in any activities further ;-)


when rebooting and after the Bios screen, a black screen appeared having only a flashing cursor.

---

### Post by hissou86 on 2010-12-10
> **amedac said:**
> You didn't provide much details, but i can try to help. Boot ubuntu from live cd, then open Gparted (System -> Administration -> Gparted) and delete all linux partitions. That should solve the problem with installing windows.

--> Thanks

I suggest for the future install OS for experimental purposes in virtual machine. :)
--> Yessssss

 .

---

### Post by sikander3786 on 2010-12-10
I would suggest to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us everything about your setup and most importantly, if that flashing cursor belongs to Grub or not.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---


---
title: "ASUS Eee PC Screen brightness issue"
date: 2011-04-10
forum: General Help
---

### Post by Perpetual_Bliss on 2011-04-10
I just installed ubuntu 10.10 (desktop version) on my netbook (Eee PC 1001p), and it works fine except for the brightness. 

Before I performed the Ubuntu recommended updates, my screen brightness was fine and exactly like what I would see in windows (I have dual boot), but after the update, my screen doesn't get bright enough. The brightest I can get now is only half of what my screen is capable off, and at the lowest setting the screen turns black.

How do I fix it so that the brightness goes back to normal? The hot keys controlling brightness and sound work fine - it's just the level of brightness that's the problem.

Thanks in advance!

---

### Post by kvarley on 2011-04-10
It may be useful to check out the Power Management settings just to check it hasn't toggled some strange settings with the update.

---

### Post by Perpetual_Bliss on 2011-04-10
> **kvarley said:**
> It may be useful to check out the Power Management settings just to check it hasn't toggled some strange settings with the update.
I checked that and it seems to be exactly the way I left it - brightness is set to 100% and the "dim the screen" box is unchecked on AC power.

---

### Post by Perpetual_Bliss on 2011-04-10
Okay, I found the solution on another forum. I'm posting it below in case anyone else has the same problem in the future:

I went to **sudo gedit /etc/default/grub**

Found the following line: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**

And replaced the "quiet splash" with "quiet acpi_osi=Linux"

The final product should look like this: 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux"**

Some people have also added on the following, but I found I didn't need to:
*"quiet acpi_osi=Linux acpi_backlight=vendor"*

---


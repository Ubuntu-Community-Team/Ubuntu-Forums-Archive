---
title: "Ubuntu 10.10 boot problem Urgent"
date: 2010-12-12
forum: General Help
---

### Post by João Oliveira on 2010-12-12
When I installed ubuntu 10.10, there was a notification to update my nvidia card with a new drive...I updated and after the reboot the screen goes to sleep but I can hear sounds!

Can anyone please help me?

---

### Post by Hippytaff on 2010-12-12
when you get to the bit of the boot where you get to choose which OS to boot, highlight ubuntu, press e and change the line with 'quiet splash' at the end to 'nomodeset'

ie delete quiet plash and type nomodeset. reboot and then remove the driver or change the nvidia settings until it works (probably resolution settings)

---

### Post by João Oliveira on 2010-12-12
I just have one OS!

---

### Post by Hippytaff on 2010-12-12
I think pressing F1 or CTRL+F1 during boot will give you the grub menu from which to press e to enter the grub thing to edit the quiet splash to nomodeset

---

### Post by sikander3786 on 2010-12-12
> **João Oliveira said:**
> I just have one OS!
Press and hold down Shift key from Bios screen until you see the Grub menu.

---

### Post by wilee-nilee on 2010-12-12
> **Hippytaff said:**
> I think pressing F1 or CTRL+F1 during boot will give you the grub menu from which to press e to enter the grub thing to edit the quiet splash to nomodeset


shift I think, works for the live cd to get the first try, install, check memory..etc ;)

---

### Post by Hippytaff on 2010-12-12
> **sikander3786 said:**
> Press and hold down Shift key from Bios screen until you see the Grub menu.
Thanks Sikander, I never can remember :-) I'm usual dual booting a different Linux distro (currently Debain)

---


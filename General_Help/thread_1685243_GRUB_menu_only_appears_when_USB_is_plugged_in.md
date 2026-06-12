---
title: "GRUB menu only appears when USB is plugged in"
date: 2011-02-10
forum: General Help
---

### Post by kc_twin on 2011-02-10
Hello,

I'm having an issue where, after having just installed Xubuntu, the GRUB menu fails to appear when the USB stick I used to install it is not plugged in. Without it, pressing ESC brings me to the Windows 7 (OS dual-booting with) special menu.

Is this standard behavior? Is the default timeout zero? Can I adjust GRUB to display for a long enough time to make a decision? Do you have any ideas as to what might be causing this?

Thanks so much for your help.

---

### Post by elliotn on 2011-02-10
it means grub has been installed in your USB

---

### Post by Mark Phelps on 2011-02-10
Standard behaviour for GRUB2, is that if there is only one OS installed (even if there are different kernel versions) is does NOT display a menu but, instead, boots into the "default" entry in the GRUB menu.

When you stick in your USB stick, that increases the number of OS's -- so GRUB2 then displays a menu.

Plus, I believe that now, you have to press a SHIFT key to force a GRUB2 menu display.

---


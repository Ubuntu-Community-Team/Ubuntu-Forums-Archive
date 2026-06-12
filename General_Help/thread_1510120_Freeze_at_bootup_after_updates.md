---
title: "Freeze at bootup after updates"
date: 2010-06-15
forum: General Help
---

### Post by fallenshadow on 2010-06-15
I had Ubuntu working perfectly until I installed two Nvidia updates. (proprietary driver)

Now Ubuntu freezes at the Ubuntu loading screen. Unfortunately I can't remember how to access the terminal at bootup, does anyone know?

Im not sure what I will try yet but I might just try getting updates in case I will get a new Nvidia update to fix this.

---

### Post by Peter09 on 2010-06-15
Hold the shift key down during boot - this gets you to the Grub menu. Then select the recovery mode and boot to the menu. Select reconfigure graphics, which with luck will allow you back into your system.

---

### Post by fallenshadow on 2010-06-15
I tried holding down the shift key at bootup twice already.

It does not work! Anyone know how to drop to a terminal at bootup?

---

### Post by Peter09 on 2010-06-15
If you have lucid this should work for Grub2.
 
Are you holding shift at the end of the bios stage so as to catch the start of grub.
If you still have grub1 its the escape key.
 
The other problem may be if you have a usb keyboard which is not being recognised during the boot phase.

---

### Post by fallenshadow on 2010-06-15
Im on Ubuntu 10.04 64bit.

I turned on my PC and held shift the whole way through but it still came to the loading screen and froze... again.

I was thinking if I could get to a terminal at bootup then I could revert the Nvidia drivers to the older one which worked!

---

### Post by fallenshadow on 2010-06-15
Beginning a fresh install... seems like the only way to solve Ubuntu problems.  :mad:

---


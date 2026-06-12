---
title: "Won't boot after installing new graphics card"
date: 2010-12-27
forum: General Help
---

### Post by hittingray on 2010-12-27
I'm running 10.10, I just recently installed a new graphics card, a Radeon HD4670, Ubuntu loads, and after it's finished loading, it goes to a black screen, and stops loading. I previously was using a nVidia 6200.

Thanks :D

---

### Post by karthick87 on 2010-12-27
On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes - then press **CTRL + X** to reboot.

---

### Post by hittingray on 2010-12-27
That gets me to a command line, what should I do after?

---

### Post by dino99 on 2010-12-27
post #2 might work, do what it says

Previously if you have tweaked xorg.conf, then you need to remove it first:

sudo rm /etc/X11/xorg.conf

then reboot

note: before removing a graphic card, always use the default driver (vesa), reboot, shutdown then replace the card

---

### Post by hittingray on 2010-12-27
Thanks very much! Deleting the xorg.conf worked.

---


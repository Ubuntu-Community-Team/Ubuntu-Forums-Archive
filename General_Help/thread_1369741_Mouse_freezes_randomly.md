---
title: "Mouse freezes randomly"
date: 2010-01-01
forum: General Help
---

### Post by HighfireX on 2010-01-01
Computer Specs:
Phenom 9500
XFX 8200 Mobo
Logitech USB infrared mouse
Microsoft Keyboard
OS:
Ubuntu 9.10 using GNOME (32 bit)

Note:
I need to use pci=nomsi in grub to boot the computer using linux

Problem:
Mouse randomly stops working
Can't go to terminal via Ctrl-Alt-F#

Details:
After a period of time my USB mouse stops working. The infrared light is still there, but no response. My keyboard works just fine, and the only way to reset it is to reset the computer. Also, when Ctrl+Alt+F#ing, It does not go to a terminal, but a blank screen. This only happens after the mouse stops working. I can still SSH into the computer even when this happens.

-Is there a way to fix this? Are there any logs that might help diagnose the problem?

---

### Post by ahood on 2010-01-09
I am experiencing the same problem on a Dell Dimension C521. If I find a resolution, I will post it.

---

### Post by ahood on 2010-01-10
I did find a solution. I googled and discovered I needed to update the bios. I did and the mouse freezing is gone. I am uncertain whether this information will be helpful. Nevertheless, I hope it is.

---


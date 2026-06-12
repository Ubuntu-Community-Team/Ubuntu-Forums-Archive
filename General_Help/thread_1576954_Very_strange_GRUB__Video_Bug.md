---
title: "Very strange GRUB / Video Bug"
date: 2010-09-18
forum: General Help
---

### Post by stuntiliator on 2010-09-18
I have just spent the past several hours trying to figure out the strangest bug. If anyone has any ideas on why this happens, PLEASE let me know!

If I attempt to boot normally, I get an "unsupported video mode" message on my monitor. However, if I hit "e" on the first grub entry, CHANGE NOTHING, and hit control-X to boot, everything boots fine and the display works. 

My video card is an onboard geforce 7050pv. I have compiled and installed the latest nvidia drivers.

Does anyone have any idea why opening the boot options but changing nothing would cause my computer to boot fine? I don't know what other path to start down.

---

### Post by Rubi1200 on 2010-09-18
Have you played around with the nomodeset option when editing the GRUB menu to see what happens?

---


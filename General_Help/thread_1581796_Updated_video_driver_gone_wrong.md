---
title: "Updated video driver gone wrong"
date: 2010-09-25
forum: General Help
---

### Post by Neliel on 2010-09-25
I recently updated my video driver after a fresh boot of 10.04 and once i restarted the system it shows everything on mymonitor up until the logon screen where the monitor just turns itself off as if there is no signal from the video card.

Anyone have any ideas on how to fix this?

---

### Post by sikander3786 on 2010-09-25
Which graphics card are you using? Which version of drivers is installed?

---

### Post by Neliel on 2010-09-25
Im using a Nvidia 9400 geforce but when i tried to edit compizconfig, it asked me to update the driver and it did it automatically, so im not sure if it did the wrong one or not. Normally I do it myself from the hardware drivers menu.

---

### Post by sikander3786 on 2010-09-25
Try this.

Press and hold down the Shift key as soon as your computer gets past the BIOS screen.

Grub menu will pop up. Select the top most entry and press "e" to edit it. 

Using arrow keys navigate to the the words "quiet and splash", delete them and type "nomodeset" in their place.

Press Ctrl and X to boot.

If the boot was successful post back. You might then need to uninstall and reinstall the graphics drivers.

---

### Post by Neliel on 2010-09-25
yeah that didnt change anything.

---

### Post by Neliel on 2010-09-25
I think i might just reformat it.

---


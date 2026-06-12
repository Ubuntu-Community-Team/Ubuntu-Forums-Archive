---
title: "NVIDIA driver - massive blocky characters on splash screen"
date: 2012-09-17
forum: General Help
---

### Post by u-noob-tu on 2012-09-17
I just installed Xubuntu 12.04 onto my desktop and I seem to have an issue with the NVIDIA drivers. On the splash screen right before the login screen, where it usually says "Xubuntu" with the dots beneath it, the text is blocky and unreadable. Yet there dont seem to be any issues when i get past that into XFCE, no obvious graphical glitches. The same thing happens when I enter into a fullscreen terminal (Ctrl>Alt>F1), its completely unreadable. I downloaded the latest NVIDIA driver for my card (GeForce 6600) from NVIDIA and tried to install it, but since i have to kill the xserver in the fullscreen terminal and the text is so unreadable i cant really tell whats going on. So i tried using additional drivers to download the post-release-updates driver. upon reboot it still showed blocky characters and my computer seemed to think i had two monitors (the top XFCE panel ran off my monitor onto an imaginary second monitor). so i reverted back to the default NVIDIA driver and am not sure what to do next. i dont recall ever having this issue before, even though i have installed Ubuntu and/or Xubuntu onto this computer several times. Could it be that the card is going bad? i certainly hope not...

---

### Post by u-noob-tu on 2012-09-20
*BUMP* any ideas?

---

### Post by mr.suchy on 2012-09-20
Hi

I have the same graphic card as you but I install older driver as you - I don't have problem like you describe. I sugest to install older driver and attachment a log file from system.

Best regards

---

### Post by kurt18947 on 2012-09-20
I'm not sure it's an Nvidia driver issue.  I haven't seen it on 12.04 but it has been a common occurrence with 12.10 for me.  I suspect it's an Nvidia hardware/Nouveau issue.  I don't think Nvidia drivers come into use until well along in the boot process.  I was also seeing the 'interesting' graphics with the Nvidia drivers unloaded.  Once the D.E. loads, the problem no longer occurs.

---


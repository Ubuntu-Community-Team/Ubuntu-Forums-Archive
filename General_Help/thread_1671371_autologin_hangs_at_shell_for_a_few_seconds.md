---
title: "autologin hangs at shell for a few seconds"
date: 2011-01-19
forum: General Help
---

### Post by joelwhrs on 2011-01-19
I created a ubuntu distro that originated from ubuntu server and have an xserver installed with openbox and am having problems getting autologin working. I had slim installed and everything seemed to be working except as soon as the monitor went into sleep mode and I moved the mouse to get it back it just came up to the shell again. With that problem I decided to remove slim and go with NODM and that worked perfectly for what I wanted but I was messing around with a few other configuration stuff and when I rebooted everything was fine until after the splash when it would normally boot into X it would show the shell for a about 10 seconds before it would boot to X. What did I mess up that is causing this? Any ideas?

---

### Post by joelwhrs on 2011-01-21
I have discovered that if I put the nomodeset into /etc/default/grub it will boot right to the X server but at a unusual resolution and it also starts up with a different plymouth theme. If anyone with more linux knowledge could help me out it would be greatly appreciated as I am in the process of selling some items with this OS on it and really need to get it finished. Thanks!!!

---

### Post by joelwhrs on 2011-01-21
Here is my /etc/default/grub file and also my Xorg.0.log file if this helps anyone. I have currently taken out the nomodeset as I need my proper resolution.

---


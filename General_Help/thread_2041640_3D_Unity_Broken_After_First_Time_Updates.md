---
title: "3D Unity Broken After First Time Updates"
date: 2012-08-13
forum: General Help
---

### Post by GBGamer117 on 2012-08-13
I just installed Ubuntu 64-bit on my HP Pavilion DV6 2011, Intel Core i7, Radeon Graphics HD(not sure which model), any extra information you need, ask. I only installed first time updates, and when I restarted the computer, I was unable to use Unity 3D. As in, it only logged in with Unity 2D. I think it is probably a driver problem, but I don't know. Please help!

Note: To be clear, I had Unity 3d before the updates.

Edit: If you have this problem, try uninstalling the drivers. It worked for me!

---

### Post by poltiser on 2012-08-13
Try in U2D reinstall ubuntu desktop - in synaptic (you need to install it from ubuntu software center)choose ubuntu desktop and install it. It should work if there are some simple mistakes. 

As well you can check the forum about radeon 3D acceleration - you might need to install radeon driver. In synaptic - drivers should be available - you need to check which radeon card is build in your laptop and choose it's driver and install.

From what you wrote it might be simple driver incompatibility, radeon is known to give trouble and you need a driver to have 3D acceleration to run U3D

U2D is nice but U3D is nicer.
I hope it helped.

---

### Post by GBGamer117 on 2012-08-13
Thanks. I'll try it after the vanilla Linux kernel is done compiling. I can't believe I didn't think to reinstall [facepalm].

Edit: After doing all that, plus installing the vanilla kernel, it still doesn't work. Let me try installing dev drivers.

Edit 2: Nope. I have now tried: Dev drivers, updating drivers, new kernel, and downgrading X.org. I shall now try downgrading drivers, but please, if you have any idea what this could be, please help.

Edit 3: Didn't Work. Oh how I wish this was an Android, so I could install Cyanogenmod and be done.

---

### Post by GBGamer117 on 2012-08-13
HAHA! I have found out the source of the problem. The drivers! Very strange, but the drivers were preventing Unity 3D from working.

---


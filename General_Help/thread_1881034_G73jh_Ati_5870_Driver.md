---
title: "G73jh Ati 5870 Driver"
date: 2011-11-14
forum: General Help
---

### Post by fnyahoo on 2011-11-14
Can you advise me how to install a driver for Ati 5870 Ubuntu 32 bit system on Asus laptop. 

The first time I tried to install, I installed it from the official Ati website, downloaded the file from the website and installed it. The problem was, after I updated the kernel (NOT UPGRADE) the driver has stopped working. I tried to fix it but couldnt so I did another clean install of ubuntu but I dont want to mess it up again. I just want the Ati drivers work after Ubuntu kernel updates. So Proper way of installing anyone. Thank you in advance.

---

### Post by Mark Phelps on 2011-11-15
Restriced driver versions are kernel-specific, so if you install from a download from the AMD site, you will have to reinstall every time you do a kernel upgrade.

However, if you use the Additional Drivers option and install that way, it gets updated with every kernel upgrade, so you don't have to reinstall.

Problem is, that version (if it is still Catalyst v11.7) is buggy and causes problems.

So, unless you really need either the 3D hardware acceleration, or other features from the restricted drivers, you woul do better using the default open-source drivers, as they work quite well now.

---


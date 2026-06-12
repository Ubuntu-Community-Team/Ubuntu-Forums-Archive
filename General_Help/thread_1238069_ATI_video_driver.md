---
title: "ATI video driver"
date: 2009-08-12
forum: General Help
---

### Post by any.linux12 on 2009-08-12
I've installed ubuntu and my graphic card doesn't look nice. My laptop's monitor is always blinking and that gives me headaches.

Laptop: Compaq 6715b
Graphic card: ATI Radeon X1250
Ubuntu 9.04 with kernel 2.6.28-14-generic

./ati-driver-installer-9-3-x86.x86_64.run 
Created directory fglrx-install.wMgVqa
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.wMgVqa

What is the problem??

---

### Post by features on 2009-08-12
Hi,

The problem is that this version of the fglrx driver is not supported by 9.04.  Unfortunately you can't use the Catalyst 9-4 and above drivers with your card (my X1300 is the same).

You can try the open source ati drivers from [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") - they are later versions which perform better.  

EDIT:  Please read the instructions on the xorg-edger's page before installing :)

Or you can do what I have done, and stay on 8.10 for now until 9.10 comes out which, from what I have experienced so far, will have excellent performance with the open source drivers

---

### Post by Janeway on 2009-08-12
Hi,

I had the same problem with my laptop and ATI Radeon X700.

You could look for the newest graphics driver on the ATI homepage, but I think there's still no driver for new Kernel 2.6.28.

I solved the problem by installing ubuntu 8.10. That comes with Kernel 2.6.27, which is supported by the driver.

But you should watch out while installing, I actually killed the entire system...

Good luck
Janeway

---

### Post by any.linux12 on 2009-08-12
> **features said:**
> Hi,

The problem is that this version of the fglrx driver is not supported by 9.04.  Unfortunately you can't use the Catalyst 9-4 and above drivers with your card (my X1300 is the same).

You can try the open source ati drivers from [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") - they are later versions which perform better.  

EDIT:  Please read the instructions on the xorg-edger's page before installing :)

Or you can do what I have done, and stay on 8.10 for now until 9.10 comes out which, from what I have experienced so far, will have excellent performance with the open source drivers

Hey! thanks a lot! I did what you told me and now works fine..

---

### Post by features on 2009-08-12
Glad it worked :D

---


---
title: "Deleted Kernel Please Help!"
date: 2011-06-01
forum: General Help
---

### Post by sherlock88 on 2011-06-01
I'm using 10.04 and had updated my kernel from 2.6.32 to 2.6.35-25, and it caused my wireless to stop working, so I tried to troubleshoot then tried putting back my previous kernel via 

apt-get install linux-image-xx.xx, 
that didn't fix it so I stupidly deleted the kernel folder in lib/modules/, rebooted and now my sound, ethernet, touchpad (I have a usb mouse though) wireless, cd...all don't work :( 

The old kernel folder is still there tho, in lib/modules/. isn't there something somewhere I can edit to have it load all the drivers and such from that folder? Or do I have to manually compile 2.6.35-25-generic from a flash drive...

Also there's no way to get on the internet until that is resolved so I can't just run a simple update or reinstall the kernel easily, can still mount flash drives.

Any help would be appreciated, i'd really perfer not to have to reinstall linux
thanks!

---

### Post by cavalier911 on 2011-06-03
When a kernel is updated the previous kernel is not removed.An additional boot stanza is added to the grub menu for the new kernel. If there is an issue with the new kernel you can choose the previous kernel in the grub menu. Unless you removed the previous kernel in synaptic/aptitude,etc. it remains on your system.
The kernel image package contains the modules you deleted.
Search synaptic on the broken computer for linux-image package.
If it's marked as installed:
Right click it/Mark for Reinstallation
If it's not marked ie. not installed:
Right click it/Mark for Installation
Download the package on computer with internet access,transfer to flash drive.
Stick flash drive in broken computer.
Synaptic:File/Add downloaded packages/browse to package on flash drive,open.
Apply

---


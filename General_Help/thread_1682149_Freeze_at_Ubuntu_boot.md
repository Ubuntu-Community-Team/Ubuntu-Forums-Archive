---
title: "Freeze at Ubuntu boot"
date: 2011-02-05
forum: General Help
---

### Post by BigTobster on 2011-02-05
Hey
 
I was tinkering around with the partition mounting setting in Ubuntu. I disabled my Windows WINRE and Windows drive being mounted at boot and left my Swap, Ubuntu and a NTFS Data drive being mounted at boot.
 
Ubuntu was booting fine before I implemented this change.
 
I then immediately rebooted (old habits die hard :) ) and the following process occurs:
 
[LIST=1]
[*]POST/BIOS runs fine. Password entered
[*]GRUB loads fine. Select Ubuntu 10.10
[*]Black screen with flashing white cursor in the top left corner(as normally expected upon boot) for around 10 seconds (slightly longer than normal)
[*]Slight flash (completely normal)
[*]Then black screen with the Linux, smaller, flashing cursor in the top left corner (as is normal). However it then doesn't move from this screen. The cursor keeps flashing away but no movement.
[/LIST]I am convinced that I have inadvertendly disabled my container volume with Ubuntu on it but not 100% sure. Even if I have, I have no idea how to fix it!
 
None of the other Ubuntu modes work (recovery or legacy). 
 
My Windows partition boots fine at GRUB if selected. This is not under the container volume.
 
Help!!!
 
Using Ubuntu 10.10
 
Thank you

---

### Post by dino99 on 2011-02-05
from the boot line, edit it and remove "quiet splash", then ctrl+x to boot. If it still fail, add either : nomodeset or noacpi. Later, check driver activation (system admin additional drivers)

---

### Post by BigTobster on 2011-02-05
Thanks for the reply.
 
1. **Deleting Quietsplash **
Goes to the small Linux cursor screen with it flashing in the middle left of the screen. No movement from this screen.
 
2. **Deleting Quietsplash and adding nomodeset**
Goes to a screen where tells you the boot information and hangs here:
Begin: Running /scripts/init-bottom ... done
[ 18.053092] rt18187: cannot register device
 
3. **Deleting Quietsplash and adding noacpi**
See 1.
 
Any other ideas?
 
Thank you

---

### Post by dino99 on 2011-02-05
seems that rtl8187 is the problem

try to open a terminal & install: nictools-pci & nictools-nopci

[http://ubuntuforums.org/showthread.php?t=1631785](http://ubuntuforums.org/showthread.php?t=1631785)

[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

this driver should better work with one of the latest kernel 2.6.38

---

### Post by BigTobster on 2011-02-05
Thanks for the reply.

2 questions:

1. How can I download the driver updates, unpack, install etc without the Ubuntu GUI? I know I have command line at GRUB but I understand that's not internet enabled?

2. I have never had issues with my Wireless and my card works out the box with Ubuntu 10.10. Also, how would a failure from a Wireless card affect the GUI boot?

Thank you for your help.

---

### Post by BigTobster on 2011-02-05
bump

---


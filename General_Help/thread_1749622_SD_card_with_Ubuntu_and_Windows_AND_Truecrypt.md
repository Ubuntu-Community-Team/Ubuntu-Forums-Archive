---
title: "SD card with Ubuntu and Windows AND Truecrypt"
date: 2011-05-04
forum: General Help
---

### Post by JigglyWiggly_ on 2011-05-04
Ok here is what I want to do.

Laptop with hard drive, has Windows XP, it is truecrypted. Then I bought a 32gb sd card, I installed Ubuntu onto it using the livecd.
But then I realized, I can't boot to it from the BIOS because the BIOS does not support booting from SD cards.

So what do I do?

I kind of want to remove the Truecrypt bootlaoder, and have GRUB take over it, but still include Truecrypt... not sure how this would work.

Maybe have a CD/USB with just the grub2 bootloader and just boot from the BIOS into that if I want to go into Windows?

This is pretty complicated since I can't boot from SD.
Halp?

---

### Post by blueridgedog on 2011-05-04
Can you install the Truecrypt boot loader onto the windows partition and then put grub in the MBR of the primary internal drive?

---

### Post by JigglyWiggly_ on 2011-05-04
Won't that like overwrite Truecrypt?

---

### Post by JigglyWiggly_ on 2011-05-04
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Ok I installed Windows 7 on the HD, just got rid of truecrypt for timebeing. Then I go into Ubuntu livecd, then it's installed onto sd card.

Then I want to install Grub onto the windows partition, so I grub-pc --purge
Then install it again, then select the hard drive, BUT THEN IT SAYS INSTALL FAILED

WAT

Then I try isntalling grub old, but I don't know how to install grub to the hard drive which has windows.
GOIN INSANE OVER HERE
Y U NO WORK

---

### Post by JigglyWiggly_ on 2011-05-04
AND TO ADD
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/703009)

When I try to install grub onto it manually
grub-install /dev/hda
I get this CANNOT STAT 'aufs'
BUT THE SOLUTION TO FIX IT IS TO CHROOT, BUT I NEVER HAD A GRUBINSTALL ON THAT HARD DRIVE, SO THERE IS NOT ANYTHING TO RECOVER
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

---


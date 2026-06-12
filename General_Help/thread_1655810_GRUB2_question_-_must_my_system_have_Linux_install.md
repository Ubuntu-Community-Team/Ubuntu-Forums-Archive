---
title: "GRUB2 question - must my system have Linux installed on the first HDD ?"
date: 2010-12-30
forum: General Help
---

### Post by Porkchop Johnson on 2010-12-30
New to GRUB... I had a single-HDD system with WinXP and Ubuntu dual-booting from grub.   I now added a second HDD, and I want to move Ubuntu to it.   

My question is, if I delete the Ubuntu partition off the first disk, would GRUB still be able to load a boot menu?     My understanding is the MBR is pretty lean and contains no state information about where any OS is located, only enough code to discover a bootloader on that same disk.  Once it has found a disk with a boot menu, then it can transfer control to other disks, but it absolutely must have some form of Linux bootloader on that first disk.

So is my understanding correct, or have I missed something ?

---

### Post by drave on 2010-12-30
linux does NOT have to be on the first drive. the code in the MBR can load the next stage from any drive.
part of the grub install/config is the call "find /boot/grub/stage1". thats what the MBR loads and it can be on any disk

---

### Post by supershin on 2010-12-30
So does that mean he can install Ubuntu 10.04/10.10(comes with grub2) and then delete the ubuntu from the 1st disk and run sudo update-grub from his new ubuntu so that only the new ubuntu and win is installed?

---

### Post by psusi on 2010-12-30
If you delete the booting Ubuntu partition from the first disk, it will break grub.  If you reinstall Ubuntu on the second disk, it will reinstall a working grub.  Also stage1 is part of grub legacy; it is no longer used in grub2.

---

### Post by supershin on 2010-12-31
Which is why i say install the new ubuntu first.

---

### Post by Porkchop Johnson on 2010-12-31
What I ended up doing was deleting the partition on the first disk, which did in fact break Grub, which tells me that apparently the MBR does contain some state information about which partition to use.

Having done that, I then booted the Ubuntu Live CD, mounted the new boot disk /dev/sdb on/newroot, then ran sudo grub-install /dev/sdb --root-directory=/newroot   That was the missing link.

---


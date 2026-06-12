---
title: "Booting ISOs with Grub"
date: 2010-08-19
forum: General Help
---

### Post by kwbauson on 2010-08-19
I've been trying to try out ubuntu maverick daily by booting the ISO from grub, so in the grub command line I run:

loopback mav (hd0,1)/testing/maverick-alternate-amd64.iso
linux (mav)/install/vmlinuz
initrd (mav)/install/initrd.gz

This boots fine, but when it gets to the point that the installer wants to read from the cd, it can't find it.  Is there a way to fix this?

---

### Post by drs305 on 2010-08-23
This is what I use for booting the ISO from my sdb6 partition, "iso" folder:

> menuentry "MAVERICK TEST ISO (hd1,6)" {
loopback loop (hd1,6)/iso/maverick-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/maverick-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


Note that it is "initrd.lz" and not .gz.  I think that changed in 9.04, but it could have been 9.10. I'm away from home and don't have the 9.04 iso to check.

---

### Post by kwbauson on 2010-08-23
Thanks, that worked fine.

---


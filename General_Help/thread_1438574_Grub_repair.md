---
title: "Grub repair?"
date: 2010-03-25
forum: General Help
---

### Post by meanmrmustard on 2010-03-25
I have two hard disks that were in a laptop together, one with Win 2K the other with Ubuntu - both of these drives are PATA.
The laptop (Thinkpad A30) died suddenly.

I've replaced the old Thinkpad with a newer model which uses SATA for the primary drive and has an ultrabay for an additional PATA hard disk.

Since the old machine was set up to dual boot, I can now no longer access (boot) either of the PATA disks by putting them in the ultrabay since the both OS's rely on the MBR from the Windows install, and Grub on the Ubuntu install.

Attempting to boot the Windows install give me the grub prompt, trying to boot the Ubuntu install tells me that I need to insert a systems disk, since (I guess) not all of Grub's stages are present.

I'm wondering what would be the best way to fix each disk so they could be booted.

If I understand correctly, I believe I could re-install Grub on the Ubuntu install and run fix MBR (or something) on the Windows drive and then be able to boot each drive from the new Thinkpad's ultrabay.
Will this work?
Is there an easier/simpler way to accomplish this?

The CD ROM has to be removed to make room for the ultrabay with the hard drives so I'm limited to using a USB version of something bootable, like Super Grub, if that's the best way

Any ideas would be appreciated.

---

### Post by byStanderone on 2010-03-25
...there's a bit of complication here since your xp was installed from another hardware (mobo), tho they say there are ways in doing what you want...grub won't be of help regarding your xp. as to the ubuntu side, try installing grub on it.

---


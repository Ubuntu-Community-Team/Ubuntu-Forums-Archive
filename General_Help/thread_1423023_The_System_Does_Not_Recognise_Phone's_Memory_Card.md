---
title: "The System Does Not Recognise Phone's Memory Card"
date: 2010-03-06
forum: General Help
---

### Post by Alvedansen on 2010-03-06
Good time of day, everyone!
I have a problem with recognising my mobile phone's memory card in Ubuntu 9.10. When I plug the phone in it starts the mass storage mode, but nothing happens in the PC. I suspect that I may have deleted phone's icon from the desktop, and I don't know how to bring it back. Also the memory card doesn't appear anywhere: nor in the Places tab, nor in Media folder.
The phone is Samsung U900 Soul, if this helps.
I'll appreciate any help!

---

### Post by Intrepid Ibex on 2010-03-06
It might be that your Phone isn't recognized. Can you post the output of "sudo fdisk -l" and check out whether Gparted sees your device - both when the device is plugged in.

---

### Post by Alvedansen on 2010-03-06
Here it is:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23747b7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

The output is the same both when the device is plugged in and when it is not.

An interesting thing is that when this Ubuntu was fresh installed, the device was perfectly recognised.

---


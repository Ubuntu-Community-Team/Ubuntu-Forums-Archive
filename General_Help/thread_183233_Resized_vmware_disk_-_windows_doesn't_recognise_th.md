---
title: "Resized vmware disk - windows doesn't recognise the new disk size"
date: 2006-05-27
forum: General Help
---

### Post by seth0x2b on 2006-05-27
Hey guys.
I used
```
 vmware-vdiskmanager -x 6Gb winxp.vmdk
```
to resize my WindowsXP guest disk.
It worked just fine and Vmware recognizes the new size, but Windows still interprets the disk as a 4Gb disk(as it was before the resize).

Do I need to follow any aditional steps after the resize?!

Thanks in advance!
Cheers

---

### Post by OliW on 2008-04-13
I know this is an old thread but it comes up near the top in Google so I thought I'd give an answer to help people who land here in the future.

After resizing the "physical size" you need to expand the partition size, just like you would if you moved a partition from a small disk to a large disk. The easiest way of doing this it booting to your Ubuntu Live CD (in VMWare) and loading up the partition editor (under system, administration). In Gparted From there, select the VMWare drive and resize the NTFS paritition.

If you don't have  Ubuntu Live CD anymore, there is a GParted Live CD that is a LOT smaller and faster as it doesn't include all the Ubuntu stuff.

GParted is pretty robust but I seriously suggest you make a copy of anything important on the image, if not an copy of the whole image.

Happy resizing.

---


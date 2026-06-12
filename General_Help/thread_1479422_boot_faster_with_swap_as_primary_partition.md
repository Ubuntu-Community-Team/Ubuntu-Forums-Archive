---
title: "boot faster with swap as primary partition"
date: 2010-05-10
forum: General Help
---

### Post by boenki on 2010-05-10
I was unsatisfied with the 40second boot time of lucid and was searching for a solution for a while but didn't find anything yet. But today I found a way to boot 10seconds quicker.

Lucid is installed here as suggested by the installer:
Primary rootpartition (/dev/sda1)
Logical partition (/dev/sda4)
swap (/dev/sda5)

I made swap a primary partition (/dev/sda2)
edited **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume** to include the new UUID
then run **sudo update-initramfs -u**

Now it boots in 30 instead of 40 seconds.

Hope it helps.

Steffen

---

### Post by srs5694 on 2010-05-10
This is very surprising. In fact, I'm more inclined to believe that you're looking at boot-to-boot variability or an effect from creating a fresh swap partition than an effect from changing it from logical to primary. The reason is that the data structures involved in defining a logical partition are not significantly more complex than those used to define primary partitions, at least not by the standard of modern hardware. If the effect really is due to the change from logical to primary, then that indicates a pretty enormous bug, or at least an embarrassing inefficiency, somewhere in some pretty basic and important Linux kernel code.

Another thought/possibility: What type of disk do you have? (Brand and model?) Some new Western Digital drives, with so-called "Advanced Format" technology, require partitions to be precisely aligned on 8-sector boundaries for optimum performance. If you've got such a disk and if the original swap partition was improperly aligned but the new one happens to be properly aligned, that could conceivably account for the effect.

---

### Post by boenki on 2010-05-11
> **srs5694 said:**
> ... that you're looking at boot-to-boot variability...

This is not a boot-to-boot variability. I have more than 20 bootchart logs before and after this. Before it was always around 40 seconds, after it always around 30.
But I'll investigate it now and create a logical swap-partition.

My harddrive is a ATA SAMSUNG HM321HI

Also this was not meant to speed up EVERYONES boot by 10 seconds, just the unexplainable slow ones, of which there seem to be a lot whith lucid.

steff

---


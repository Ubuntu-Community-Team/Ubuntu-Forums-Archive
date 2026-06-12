---
title: "move /boot"
date: 2006-05-03
forum: General Help
---

### Post by xiaoxin on 2006-05-03
Hi

Standard ubuntu puts all folders under /
but i want to move my /boot to a separate partition.
How can i make this work? 
I already made the partition and copied the boot folder there.
I gues i have to run a grub-install but with what parameters?
How can i tell it the location of the new boot folder?

---

### Post by neouser99 on 2006-05-03
you have to do two things (i think):

1. update your fstab to mount or not mount this (doesn't really affect the booting of the kernel, just the operation after its booted)
2. change the device.map inside the grub. this can be done with a ```
grub-install --recheck <dev>
```after that, just make sure that your menu.lst is setup properly.

-neo

---

### Post by Ramses de Norre on 2006-05-03
I found this:> 11. I have a separate boot partition on GNU/Linux (or another UNIX-like system), and GRUB seems not to handle this situation correctly.

This is often reported as a bug, but this is not a bug really. This is a feature.

Because GRUB is a boot loader and it normally runs under no operating system, it doesn't know where a partition is mounted under your operating systems. So, if you have the partition /boot and you install GRUB images into the directory /boot/grub, GRUB recognizes that the images lies under the directory /grub but not /boot/grub. That's fine, since there is no guarantee that all of your operating systems mount the same partition as /boot.

There are several solutions for this situation:

   1. Install GRUB into the directory /boot/boot/grub instead of /boot/grub. This may sound ugly but should work fine.
   2. Create a symbolic link before installing GRUB, like cd /boot && ln -s . boot. This works only if the filesystem of the boot partition supports symbolic links and GRUB supports the feature as well.
   3. Install GRUB with the command install, to specify the paths of GRUB images explicitly. Here is an example:

            grub> root (hd0,1)
            grub> install /grub/stage1 d (hd0) /grub/stage2 p /grub/menu.lst
            



---


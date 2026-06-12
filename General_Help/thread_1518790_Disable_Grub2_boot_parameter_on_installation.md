---
title: "Disable Grub2 boot parameter on installation?"
date: 2010-06-27
forum: General Help
---

### Post by XP1 on 2010-06-27
**Disable Grub2 boot parameter on installation?**

Is there a boot parameter that I can enter in the advanced boot options of the installation disc so that I can skip the Grub2 upgrade and stay with Grub1?

Grub2 freezes **_[my computer]("http://ubuntuforums.org/showthread.php?t=1518743")_** and prevents it from booting.

---

### Post by dino99 on 2010-06-27
grub2 cant work with grub1: so remove/purge everything about grub but grub-pc & grub-common, remove menu.lst too if it still exist

then :
 sudo grub-mkconfig
 sudo update-grub

grub2 is the default since karmic and might your only choice. Do the above commands and reboot

note: if grub2 freeze, edit the boot line and remove "splash", that should do the trick; if not, run : sudo blkid to identify the uuids and compare with the ones into fstab

note2: if you have a multiboot, install grub2, when asked, on the same ubuntu partition

---

### Post by XP1 on 2010-06-27
> **dino99 said:**
> grub2 cant work with grub1: so remove/purge everything about grub but grub-pc & grub-common, remove menu.lst too if it still exist

then :
 sudo grub-mkconfig
 sudo update-grub

grub2 is the default since karmic and might your only choice. Do the above commands and reboot

Ok, maybe I would first like to have grub2 if I can fix the freeze. If not, then I am forced to stay with grub1.

> **dino99 said:**
> note: if grub2 freeze, edit the boot line and remove "splash", that should do the trick; if not, run : sudo blkid to identify the uuids and compare with the ones into fstabI removed the "splash" from the **/boot/grub/grub.cfg** file. It did not work.

Next, I compared the UUIDs from **/boot/grub/grub.cfg** and **sudo blkid**. They were the same. The **/etc/fstab** file did not have any UUID for sda1 (only UUID for swap).

> **dino99 said:**
> note2: if you have a multiboot, install grub2, when asked, on the same ubuntu partitionI do not have a multiboot setup.

I also tried "Unhide/Hide the Menu" _[here]("http://ubuntuforums.org/showthread.php?t=1302743")_, but it did not work.

I also tried setting the grub2 resolution to 640x480:

Then, using _[http://ubuntuforums.org/showpost.php?p=9513124&postcount=8](http://ubuntuforums.org/showpost.php?p=9513124&postcount=8)_ from Lubuntu 10.04 Live CD:```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
sudo update-grub
```

It still freezes. :confused:

---


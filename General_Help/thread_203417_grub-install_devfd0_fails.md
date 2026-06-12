---
title: "grub-install /dev/fd0 fails"
date: 2006-06-25
forum: General Help
---

### Post by cotcot on 2006-06-25
Hi,
I have a dual boot with the bootloader on floppy. In breezy it was as simple as ```
sudo grub-install /dev/fd0
``` to install the bootloader on the floppy.

Now using dapper on my PC2 (see signature) i get the error > Could not find device for /boot: Not found or not a block device. with the same command.  (I do not want to to upgrade from breezy to dapper on my PC1 untill this is ok.)

Any idea why ?

---

### Post by cotcot on 2006-06-25
Problem is not solved but I tried another way to achieve the same goal.

I used the LiveCD (install CD Dapper).

```
sudo su
grub
root (hd0,2)
setup (fd0)
``` 

where (hd0,2) is grubs language for my partition hda3. I have /boot/grub on this.

---


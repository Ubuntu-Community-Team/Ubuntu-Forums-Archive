---
title: "grub posinit hook script error 139 segfault"
date: 2009-12-11
forum: General Help
---

### Post by Teleken on 2009-12-11
Hi,

Not sure what I did here, but I can't do apt-get updates anymore and my system won't boot on it's own because any attempt by the system to update the boot image (i.e. to add the commands to mount my raid) will fail with the following error:

```
Setting up linux-image-2.6.31-16-server (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-server
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.31-16.52 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.31-16.52 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Segmentation fault
User postinst hook script [/usr/sbin/update-grub] exited with value 139
dpkg: error processing linux-image-2.6.31-16-server (--configure):
 subprocess installed post-installation script returned error exit status 139
```and the following commands illustrate the grub problem:

```
root@phalanx:~# grub-probe -v -d /dev/mapper/phalanx-Perspicacious
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: opening phalanx-Perspicacious
grub-probe: error: Physical volume pv1 not found
root@phalanx:~# grub-probe -v -d /dev/mapper/phalanx-Perspicacious -t abstraction
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: the size of hd0 is 488397168
grub-probe: info: opening phalanx-Perspicacious
Segmentation fault
root@phalanx:~# cat /boot/grub/device.map
(hd0)   /dev/sda
```However I have no idea what to do from here.  I've done searches, found other people with similar problems but no solutions.  Any help would be greatly appreciated!  Thanks!

---

### Post by Teleken on 2009-12-13
I hate to bump but there are five trillion people reading this site and I have found nothing else to help me - there must be someone who can offer some advice?  Thanks in advance!

---

### Post by tvdnagel on 2009-12-30
Don't know if you still need a solution, but here's what helped me when I got the same error:

sudo apt-get install --reinstall grub

The re-install of GRUB helped me to solve the error.

---


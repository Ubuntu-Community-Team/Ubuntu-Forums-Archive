---
title: "Is this a bad output for update-grub?"
date: 2011-01-24
forum: General Help
---

### Post by silkworm2.5 on 2011-01-24
Hi all.
I recently had some problems with grub and had to reinstall with the live CD - chroot method. Now I'm back in Ubuntu, and I ran update-grub, but I get this output.

```
silkworm205@Felicia:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found memtest86+ image: /boot/memtest86+.bin
[B]ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory[/B]
Found Windows Vista (loader) on /dev/sda2
Found Ubuntu natty (development branch) (11.04) on /dev/sda7
done

```Am I going to have trouble when I reboot?
It's Grub 1.98, Ubuntu 10.04.


EDIT: It's fixed now. There was a folder there from trying to install Grub, and it was boot in lower case, and Windows is not case sensitive.

---

### Post by Quackers on 2011-01-24
I think it's caused by /boot/grub/core.img being in the Ubuntu partition (from installing grub there).

---


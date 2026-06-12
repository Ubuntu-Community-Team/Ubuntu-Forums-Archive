---
title: "GRUB - incorrect menu"
date: 2011-06-03
forum: General Help
---

### Post by fantab on 2011-06-03
I am having weird problem with Grub Menu listing during Grub display at Boot. I Multiboot with Lucid Lynx, openSUSE and Windows7. My Grub is installed along with Ubuntu. I did not install bootloader when installing openSUSE. 

Now during boot Grub Menu displays** five entries for openSUSE**. However when I did grub-update in the terminal it shows only one image for openSUSE in terminal.

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found Windows 7 (loader) on /dev/sda1
Found openSUSE 11.4 (x86_64) on /dev/sda3
Found memtest86+ image: /boot/memtest86+.binBut again **Grub Customizer** shows or lists **five entries for openSUSE**. (Please see the attached screenshot)

There are no problems during boot (except that Ubuntu takes a bit longer to load). **I am really annoyed by the multiple SUSE entries in the GRUB and also by the fact that Ubuntu takes a bit longer than normal to boot. **

Please help me to get rid of these annoyances.

---

### Post by plucky on 2011-06-03
All it is probably doing is showing different kernel updates.

You can probably login to Opensuse and use its package Manager to remove the earlier kernels and once they are removed,Grub in Ubuntu (when you run "sudo update-grub")will not find them and will not display them in the Grub Menu.

It is always a good idea to keep at least one older kernel to boot into if you break the current working kernel.

You will also find that when the kernels are upgraded in Ubuntu,they will also be displayed in the Grub Menu.

Good Luck

---


---
title: "Duplicates in Grub2 Menu"
date: 2012-06-04
forum: General Help
---

### Post by neopiper on 2012-06-04
I removed the background image from the Grub on a Windows 8 and Ubuntu dual boot machine.  I then run the command "sudo update-grub" and now I'm having duplicates on my grub menu.  This is how it looks like.


Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found Windows 8 (loader) on /dev/sda1
Found Windows 8 (loader) on /dev/sda1


How can I solve this?

---

### Post by drs305 on 2012-06-04
Have you copied any of the files (scripts) in /etc/grub.d ? If you had two copies of the scripts they would both run and add the results you see (10_linux and 30_os-prober).

---


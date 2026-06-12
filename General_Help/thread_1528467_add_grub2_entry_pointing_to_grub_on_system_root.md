---
title: "add grub2 entry pointing to grub on system root"
date: 2010-07-10
forum: General Help
---

### Post by nucleuskore on 2010-07-10
Hi
I have a netbook with the following three OSes

Windows XP
Ubuntu 10.04
Ubuntu 9.10

Now the grub bootloader is provided by Ubuntu 10.04. I installed 9.10 later with grub on the root partition of the same. I booted into Ubuntu 10.04 and then did a sudo update-grub
This automatically created a singular entry in the grub bootloader on the mbr which enables me to boot Ubuntu 9.10

Now my question is

What entry would I have to make to the 40_custom file in /etc/grub.d such that ann entry is created in the main grub bootlooader, which gives me access to grub on the root partition?

---

### Post by mikewhatever on 2010-07-10
All the working grub entries, for Windows and both Ubuntu installations can be found in /boot/grub/grub.cfg. You can copy the one you want from there and place it into /etc/grub.d.

---


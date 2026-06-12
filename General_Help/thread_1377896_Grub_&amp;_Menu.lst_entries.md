---
title: "Grub &amp; Menu.lst entries"
date: 2010-01-10
forum: General Help
---

### Post by AllanP on 2010-01-10
I have 9.10 on my laptop, but hesitate to put it on here as I have generic menu.lst entries for Fedora and Suse. In other words when I upgrade either; or kernel changes I don't have to edit menu.lst. However with this new system I don't see how I can edit and put my generic entries into the new grub. I know how to change default OS and menu delay and that's about it. Or is there something simple that I am missing like update grub after an OS changes kernel ID?

---

### Post by vinnywright on 2010-01-10
you can install withought the new grub and add to the menu.lst of wichever one of you'r other OS's that controle grub now.......and add with the same genarick lines you use now IE: the system link's in / for vmlinuz and initrd.img

and yes update-grub works with both grub and grub2

VINNY

---

### Post by AllanP on 2010-01-10
> **vinnywright said:**
> you can install withought the new grub and add to the menu.lst of wichever one of you'r other OS's that controle grub now.......and add with the same genarick lines you use now IE: the system link's in / for vmlinuz and initrd.img

and yes update-grub works with both grub and grub2

VINNY

Are you saying that I can install 9.10 with the old "menu.lst"

and regarding update-grub: does that command update the info from the other OS's menu.lst's?

TIA

---


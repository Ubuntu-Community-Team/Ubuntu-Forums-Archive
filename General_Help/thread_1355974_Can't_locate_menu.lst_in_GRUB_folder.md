---
title: "Can't locate menu.lst in GRUB folder"
date: 2009-12-15
forum: General Help
---

### Post by jakekimpton on 2009-12-15
Ok so i was going to change the boot order in the menu.lst file when i noticed that i don't even have a file called menu.lst in the /boot/grub/ dir. How come? 
It confuses me as GRUB works, but there clearly isn't a menu for it...

Some help with this would be lovely. Thanks.

---

### Post by ean5533 on 2009-12-15
> **jakekimpton said:**
> Ok so i was going to change the boot order in the menu.lst file when i noticed that i don't even have a file called menu.lst in the /boot/grub/ dir. How come? 
It confuses me as GRUB works, but there clearly isn't a menu for it...

Some help with this would be lovely. Thanks.
Grub 2 (installed by default in Karmic 9.10) works different than legacy grub.

See **[this thread]("http://ubuntuforums.org/showthread.php?t=1195275")** for a complete listing of the differences and how to deal with it.

---

### Post by Wardje on 2009-12-15
As said in the previous post, grub legacy (that's grub 1 (or 0.97 to be exact)) is the grub version using that file. Grub 2 does not.

You can check your grub version by opening a terminal and typing
```
grub-install -v
```
"GRUB 2 should display a version number of 1.96 or later. Legacy GRUB is version 0.97."

---

### Post by jakekimpton on 2009-12-16
Ok  my install of grub was 0.97 so i upgraded to GRUB 2 and managed to edit the default boot order. I didn't realise i was using an older GRUB before hand. Thanks

---


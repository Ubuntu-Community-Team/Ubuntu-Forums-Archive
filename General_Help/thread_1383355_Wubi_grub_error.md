---
title: "Wubi grub error"
date: 2010-01-17
forum: General Help
---

### Post by Newbie6 on 2010-01-17
I have installed Kubuntu 9.10 through Wubi. I have Windows 7, but want to try out Kubuntu. I had it up working for 1 week, but after the last update I get this message when trying to boot into Kubuntu: 

GNU GRUB version 1.97~beta4

Minimal bash-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.

sh:grub>

I have read a lot about this error and have tried out a few things without success.

If I use the command ls, I get this message:
(loop0) (hd0) (hd0,6) (hd0,5) (hd0,4) (hd0,2) (hd0,1)

and with the command ls /boot, I get:

2.6.31-17-generic-pae

I have tried to use this command at the grub prompt:

set root=(loop0)
linux /boot/vmlinuz-2.6.31-17-generic-pae root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-17-generic-pau
boot

I starts ok, but when I use the command boot, it stops after a little while and writes a lot. I have noticed these sentences:

unable to mount root fs on unknown-block (8,5)

2.6.31-17-generic-pau swapper not tainted #54 Ubuntu

I tried changing sda1 to sda2, sda3, sda4 etc. without luck so far ....

I really hope someone can help me solve this problem so I can start using Kubuntu again [IMG]http://kubuntuforums.net/forums/Smileys/classic/smiley.gif[/IMG]

---

### Post by nivrex on 2010-01-27
you could try this if you haven't solved the problem it yet .
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---


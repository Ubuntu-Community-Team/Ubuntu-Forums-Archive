---
title: "virtual console customization"
date: 2010-09-30
forum: General Help
---

### Post by einstenian on 2010-09-30
Hi all.
I'm writing from ubuntu 10.04. When switching to a virtual console with ctrl+alt+f1, i enter in a virtual console. I would change his aspect, in particular i would set the resolution and the fonts in such a way they match the same parameter used when booting the system ( i login in text-mode on my server). How can i customize the console? I tried the command```
 sudo dpkg-reconfigure console-setup
``` but it give me only the possibility to change the font size to a smaller value.

any tip?

addendum : solved. It is sufficient to edit the grub conf file:

sudo gedit /etc/default/grub

chenge the line 

GRUB_CMDLINE_LINUX_DEFAULT=""

to

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

saving and giving:

sudo update-grub

---


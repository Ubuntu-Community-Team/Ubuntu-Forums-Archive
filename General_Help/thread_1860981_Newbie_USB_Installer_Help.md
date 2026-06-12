---
title: "Newbie USB Installer Help"
date: 2011-10-15
forum: General Help
---

### Post by zenarcadian on 2011-10-15
Howdy, my name's Mike, and I've just made a pendrive installer for the latest Ubuntu for my netbook (Samsung n130).
 
Any time I go to install Ubuntu through Wubi, though, it fails to boot. The Demo and Installation option fails to bring up the OS selector menu, and goes straight to XP.
 
Installing inside Windows fails too, bringing up the alert:
 
"WindowsBackend" has no attribute "isopath"
 
What am I doing wrong exactly? And what have I to do to obtain Netbook Remix?

---

### Post by zenarcadian on 2011-10-15
Bump!

---

### Post by Blaqksheep on 2011-10-15
It sounds like when you installed, you picked the option "Something Else" because it mentioned selecting your partitions and such.  The problem you are having is that grub, the screen that appears early in the boot that allows you to switch your OS, is not installed.  If you have a lot of customizations from your first boot, I suggest looking for one of the threads around repairing/restoring grub.  If you don't have any major changes or saved documents, I suggest just reinstalling Ubuntu using the first option, "Install alongside Windows".  The first option *should* install grub just fine, while the "Something Else" assumes you know what you're doing grub-wise.

[EDIT]Correction.  "Something Else" will also install grub for you, however, you have to tell it which partition to install it to via dropdown box.

---


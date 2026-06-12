---
title: "Removing the splash screen"
date: 2009-07-08
forum: General Help
---

### Post by Dylan Bartlett on 2009-07-08
Hey. Im running Heron and i am wondering if anybody knows how to disable the splash screen on startup so i can see the text? No major reeason i just want the instead :lolflag:

---

### Post by moster on 2009-07-08
```
sudo gedit /boot/grub/menu.lst
```


and remove word "splash" from your kernel line. Here is mine.

```
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=45af080e-c43b-4032-ad16-74d6da086023 ro quiet **splash**
```

---

### Post by fooman on 2009-07-08
there are a few methods to do this....

to disable on a per-use basis,  wait for the splash screen,  then press alt-f1 to make disappear for that boot.

to disable it permanently...you will need to edit the /boot/grub.menu.lst file to remove both "guiet" and "splash" from the kernel line.... 

open a terminal and type or copy/paste the following:

```
gksudo gedit /boot/grub/menu.lst
```when it opens,  scroll down to the latest kernel,  find the "kernel" line and remove both (AND ONLY) "quiet" and "splash" from the line....save and exit.

or, if you want a nice, easy gui (no command line or editing files),  use "startup-manager"...it is in synaptic (system > administration > synaptic package manager,  search for "startupmanager").  or just open a terminal and type or copy/paste:

```
sudo apt-get install startupmanager
```after it installs, go to system > administration > startup-manager

when it opens,  look on the boot options tab and *un*-check "show boot splash"

hope that helps.

---


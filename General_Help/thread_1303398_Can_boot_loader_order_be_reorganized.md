---
title: "Can boot loader order be reorganized?"
date: 2009-10-28
forum: General Help
---

### Post by zzprop on 2009-10-28
I have ubuntu 9.04 loaded on the family computer in its on partition.
When the computer shuts off, as in a power fail,  my family members only know how to push the power button to turn it on. Well if I'm not here and the dual boot screen comes up I don't want one of them to have to do anything but hit enter to load windows. 
I have windows first loaded on this computer and then loaded U on second. U is on the top of the list for boot and I don't want them to have to select windows with the arrow key.
can I rearrange the list and put windows on top?

If I install 9.04  with wubi I still have a boot select screen don't I? 
Speaking of loaded inside of windows, which I really don't want to do, would my windows virus software also protect ubuntu while it is running inside windows?

Thanks 
zz

Hey you can teach an old dog new tricks.

---

### Post by Bucky Ball on 2009-10-28
You will not need virus protection for Ubuntu and Wubi installs are clunky and yes, once installed you can change the grub menu order.

You need to go to a terminal and type:

```
nano /boot/grub/menu.lst
```That is the file you need to change. Have a look and get familiar then close it. Now type:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```This makes a backup of your menu.lst before you change anything, just in case, then:

```
sudo nano /boot/grub/menu.lst
```You can move the OS entries to any position you want. Just be careful to move the whole thing. As long as the correct syntax is there, doesn't matter where it is.

---

### Post by The Cog on 2009-10-28
Each OS option consists of a group of 4-5 lines - title, whcih partition etc. You could edit the file so your preferred option is the top one. Remember the "automagic" section gets rewritten every time there is a kernel update.

Or you can change the default (usually 0 meaning the first option) rather than shuffle the other options around, but remember that an update will add a new entry into the automagic section which will renumber all the options below it.

So overall, it's probably best to move the windows stanza to newr the top before the automagic section.

---


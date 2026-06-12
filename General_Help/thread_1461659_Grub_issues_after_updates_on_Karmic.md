---
title: "Grub issues after updates on Karmic"
date: 2010-04-24
forum: General Help
---

### Post by OmegaPanncake on 2010-04-24
I'm having a problem with Wubi on my netbook, and while I could fix it easily (though probably only temporarily) by reinstalling, I've been using it since January and many of the files are files I cannot afford to lose.

I'm dual booting with Windows XP, but when I choose Ubuntu 9.10 from the menu at startup, it takes me straight to Grub with the following message:

> GNU GRUB version 1.97~beta4
[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]
sh:grub>

I've had this problem once before, but I was able to fix it with the wubildr patch. Both instances of this problem have occurred after updates, though it hasn't happened after every update, just the two so far.

I've also tried several of the command-line suggestions that have fixed this problem for other users, but I've been getting "unknown filesystem" when I attempt them.

If anyone has any idea how to fix this without losing the files I have on my current install, please help!

---

### Post by P4man on 2010-04-24
Wubi guide gives some tips on fixing grub issues and accessing files through windows:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Cant really help more than that, since I have zero experience with wubi, I would just strongly advice your next install to be a regular one, and not a wubi one.

---


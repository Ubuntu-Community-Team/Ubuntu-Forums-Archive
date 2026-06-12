---
title: "Two grubs? Dual boot Crunchbang + Xubuntu (kuki)"
date: 2010-03-05
forum: General Help
---

### Post by Pott on 2010-03-05
I was originally running Kuki, which is essentially a Xubuntu distro optimized for my Acer AA1. I'm dual booting (on a 8GB SSD!) with Crunchbang, which is actually my default choice now. 

So basically now I have two grubs. The one that came with #! is acting as default now, so I'm not having any actual issues. But I'm wondering if this could be an issue later on? I won't triple boot or modify my Grub (#!) further really.

As far as I understand Linux, it seems to have picked up onthis automatically and disabled the first grub to let the second instance do its work just fine but I'm not quite sure...

---

### Post by ajgreeny on 2010-03-05
You will probably be running legacy grub or grub2 from whichever OS was installed last.  If you prefer the other just boot to it from grub, and then run ```
sudo grub-install /dev/sda
``` assuming sda is your disk name.  You can swap around that way as much as you wish, as I have done in the past with Ubuntu and Mint.

---


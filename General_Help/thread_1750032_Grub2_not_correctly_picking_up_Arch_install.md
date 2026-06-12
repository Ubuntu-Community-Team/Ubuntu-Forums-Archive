---
title: "Grub2 not correctly picking up Arch install"
date: 2011-05-05
forum: General Help
---

### Post by TMC on 2011-05-05
I'm experimenting - for the first time - with dual booting.

I have Ubuntu 10.04 already installed and have installed Arch in a spare partition.  When I run sudo update-grub, I get the following 

david@laptop-work:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /memtest86+.bin
Found Arch on /dev/sda4
done
david@laptop-work:~$ 

so it appears to be correctly finding and identifying Arch, but when I boot up, I just get an extra copy of the Ubuntu entries in the Grub menu, just suffixed with " (on /dev/sda4)" and they boot into Ubuntu.

Checking grub.cfg, these entries are just carbon copies of the regular Ubuntu entries.

I've tried Googling, but nothing seems to be relevant (then again, I know so little about Grub2 that, in all honesty, I don't really know what would be relevant).

Any pointers as to where I can find out how to get this to work?

Many thanks,

David Shaw

---

### Post by TeoBigusGeekus on 2011-05-05
Install grub legacy from the arch cd on your arch partition (sda4). Then try again to run update-grub: it should recognize the arch bootloader and chainload to it.

---

### Post by TMC on 2011-05-06
Many thanks.  It took me a while to figure out how to do that, but when I didi, it worked like a charm.

David Shaw

---


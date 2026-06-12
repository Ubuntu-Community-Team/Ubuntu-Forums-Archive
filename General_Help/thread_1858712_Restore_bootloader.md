---
title: "Restore bootloader"
date: 2011-10-12
forum: General Help
---

### Post by cclloyd9785 on 2011-10-12
I had to clean install windows, and it rewrote the windows loader to the mbr.  

Using a live CD, how can I rewrite the linux bootloader as the first one.

Note:  Its on dev0, sda3.

---

### Post by cryptotheslow on 2011-10-12
Provided you didn't manage to obliterate your Ubuntu install and partitions completely when installing Windows this should help:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

If unsure what state your partitions are now in - from your Live CD environment follow this:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

... and post up the contents of the RESULTS.txt file contained within CODE tags (the # button on the toolbar when posting a reply).  This will give assisters the best chance of understanding what is going on with your partitions and boot loader configurations so to provide relevant advice.

Good luck.

---


---
title: "GRUB2 and Haiku"
date: 2009-10-28
forum: General Help
---

### Post by Ilovepenguins on 2009-10-28
Hey guys! Just did a clean install of karmic and it came with grub2. I previously had Jaunty with grub1 and I was dual booting Haiku just fine. I know that there is a different procedure to adding other OS's in grub2 and I tried to follow the instructions very closly. I went to /etc/grub.d and made a executable file called 11_Haiku. In this file I wrote: ```
#! /bin/sh -e

echo "Adding Haiku entry" >&2
menuentry "Haiku" {
    set root=(hd0,8)
    chainloader +1
}


```

Because Haiku is on sda9.
But when I do ```
sudo update-grub2
```
I get ```
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Adding Haiku entry
/etc/grub.d/11_haiku: 4: menuentry: not found

```

And when I reboot I don't even see the grub menu.
Sorry if this has been asked before or I'm making a really dumb error somewhere, I'm really new to grub2.
Thanks for your help

---

### Post by drs305 on 2009-10-28
Grub 2 counts partitions differently. Partition 1 is now 1. Drive 1 is still counted as 0. So if it's on sda9, the entry would be (hd0,9).

There are links in my signature line about various aspects on Grub 2. The first one links to the community doc and provides explanations as well as a few graphics.

---

### Post by Ilovepenguins on 2009-10-28
ok, I just went back to grub1. Works fine now. Thanks for your help anyways, it may help someone else.

---

### Post by koki on 2010-09-10
In case anybody else is interested in adding Haiku to GRUB2, here is how it's done:

[http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10](http://haikuzone.net/tips/installation/adding-haiku-grub2-ubuntu-9.10)

Hope this helps!

---


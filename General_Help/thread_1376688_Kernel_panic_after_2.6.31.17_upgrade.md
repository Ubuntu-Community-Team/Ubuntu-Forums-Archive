---
title: "Kernel panic after 2.6.31.17 upgrade"
date: 2010-01-09
forum: General Help
---

### Post by jaezcurra on 2010-01-09
After an (supposed) successful upgrade from 2.6.31.16 to 2.6.31.17 9.10 under Wubi, there is a kernel panic after the suggested reboot.

Fortunately I had an 2.6.31.16 entry in Grub 2 and I can keep on working in Ubuntu.

---

### Post by jaezcurra on 2010-01-09
I found the fix in [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)
and, to be precise, in comment 194:
[http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/194](http://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/194)
Thanks, Agostino Russo :D

---

### Post by Aiolos on 2010-01-10
I second Jaezcurra, comment #2.  Fetched "wubldr" from [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90), overwrote C:\wubldr and shut down. On next startup GRUB menu appeared and I booted 2.6.31.17 successfully, the kernel upgrade that halted GRUB 1.97~Beta4 Jan 6. Following other users of this fix, I did not edit the GRUB menu option 2.6.31.17, that is, did not erase "insmod ntfs" as Russo recommended. I am back in business. (See [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/200](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/200), however.)

The Wubi partition I recovered is SDB5, 25 Gig.. SDA1, Win 2000, is the only Primary partition in my system, of which all partitions except Ubuntu are formatted NTFS.

---


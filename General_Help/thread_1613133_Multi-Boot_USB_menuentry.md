---
title: "Multi-Boot USB menuentry"
date: 2010-11-04
forum: General Help
---

### Post by ziazis on 2010-11-04
Hey guys,

so i got a problem with the grub2 menuentry for the dban-2.2.6_i586.iso.

Well since i'm really new to the whole Ubuntu things (about 1 month now -  that i'm working with it), I thought of rather ask a Forum for help  then searching in the nowhere :).

> menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-2.2.6_i586.iso
 linux    (loop) /dban.bzi nuke="dwipe" silent --
}
I've already succeed in booting kubuntu.iso from my USB, however dban isn't working...

I hope u guys help me out.

---


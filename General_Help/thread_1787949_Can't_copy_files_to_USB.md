---
title: "Can't copy files to USB"
date: 2011-06-21
forum: General Help
---

### Post by Neodarkness on 2011-06-21
Hi.
I'm having a really nasty problem with my laptop. Every time I try to copy a file to a Pendrive it fails, making the USB read-only or ejecting it without my consent (after which I have to physically unplug it and plug it back for it to even appear at nautilus again).
I discovered that I CAN copy files if I do it with dd as in:

"dd bs=4096 if=The.Tunnel.2011.Xvid-VODO.avi of=/media/AA5D-8F2D/The.Tunnel.2011.Xvid-VODO.avi"

I think it the problem is related to the copy bitrate...
Any clues?

Thanks
(also: it happens both in ubuntu and arch linux)

---


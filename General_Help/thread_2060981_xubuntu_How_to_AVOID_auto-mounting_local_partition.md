---
title: "xubuntu: How to AVOID auto-mounting local partitions?"
date: 2012-09-21
forum: General Help
---

### Post by homyakchik on 2012-09-21
[FONT="Courier New"]Howdy, all
I currently run ubuntus in a VM on my main machine (so far, still working) and on a spare drive on my laptop (the 'for real' one). Yesterday, after about a week of troubleshooting apps just not working any more, I slicked the drive. I installed DOS in a teeny partition (old programming tools, hobbyist, stuff like that). After ubuntu 12.04 wouldn't even boot from the CD, I found that Xubuntu was a viable (and bootable) alternative. Installed it this morning, and have been slowly recovering my setup (reinstalling native apps first).

Among other interesting quirks, though: the DOS setup has a C:, D:, E: and F: drive (all in the 8 gigs DOS limit). These are just for the DOS boot; I can conceive of no reason whatsoever to want to access them directly in my *nux desktop. Nonetheless, xubuntu's faithfully mounting them at startup. I can right-click and be given the options of OPEN and MOUNT, and sure enough see the drive's contents.

What I'd *like* is to have xubuntu *stop* mounting the drives. I found tons of posts on how to convince the OS to auto-mount a drive or partition or something, but I don't see anything that tells me how to tell the OS to *not* mount the silly things.

Is this possible? I'm assuming it is; linux seems to have almost every eventuality covered.

Thanks!

Davey[/FONT]

---

### Post by Toz on 2012-09-21
I use the following config (/etc/udev/rules.d/hide-partitions.rules) file to hide my windows partition. The contents of this file are:
```
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"
```

You'll need to add a line for each partition that you want to hide _and_ replace each instance of **sda1** with the actual partition that you want to hide.

---


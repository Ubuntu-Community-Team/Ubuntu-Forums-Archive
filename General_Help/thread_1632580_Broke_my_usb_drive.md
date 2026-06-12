---
title: "Broke my usb drive"
date: 2010-11-28
forum: General Help
---

### Post by dexusnl on 2010-11-28
Yesterday, the file system of my mp3 player went corrupt.
So I tried to format it to vfat, which in the past hasn't solved the problem and instead just made another corrupt partition.
I have fixed it before by using dereks boot and nuke (dban) and filling it with only zeros so its ready to be repartitioned.

Now this time I tried to save some time by using dd instead of dban.
So I did dd if=/dev/zero of/dev/sdb

The process got interrupted by my system shutting down after about 15 min.

Now when I plug in my usb, it doesn't get recognized.
It doesn't show up in gparted or fdisk.
I looked at dmesg and all it gave was:
usb 1-4: new high speed USB device using ehci_hcd and address 5

How do I fix it? I don't know how to tackle this

---

### Post by iNsOmNiOuS on 2010-11-28
Had almost the same problem as you, MP3 was no longer recognized after failed repartioning. I never found a solution to this, and it ended up in the bin =(

---


---
title: "IDE Woes"
date: 2006-03-21
forum: General Help
---

### Post by ngms27 on 2006-03-21
I have two IDE drives on the same channel.

Despite setting them both for DMA in hdparm.conf it would seem only one drive can use DMA.

Is this correct?

Obviously this makes file transfers between drives very slow.

---

### Post by dcstar on 2006-03-21
[QUOTE=ngms27]I have two IDE drives on the same channel.

Despite setting them both for DMA in hdparm.conf it would seem only one drive can use DMA.

Is this correct?

Obviously this makes file transfers between drives very slow.[/QUOTE]
You must meet (at least) two requirements for DMA to work:

Firstly the BIOS must have DMA enabled for that device, and secondly;

The device must also support DMA (just about everything less than 4 or 5 years old will).

sudo hdparm -I /dev/hda (or hdb, c or d) will show you what Ubuntu thinks the device is capable of.

---


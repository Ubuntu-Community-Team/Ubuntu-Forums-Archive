---
title: "Brand new MicroSD protected from writing"
date: 2009-10-05
forum: General Help
---

### Post by guedesav on 2009-10-05
(Moved in here from "Laptop and Hardware" by the author)

Hi, I saw a few other threads on the subject, but none have a solution, so I decided to start from scratch.

So, I have a MicroSD that works fine here. Then I decided to buy a new one, a SanDisk, and found out it was write-protected. I thought it was something of the manufacturer, so I bought another Kingston(just as the one I have and works fine), but it's also write-protected.

This one that works is accessed through an SD adapter, and both others accuse protection, even though they're both new. I even tried them on Vista, but they can't be formatted either. And, yes, I've checked the "Lock" switch on the adapter.

Here's the line on fstab for the SD cards:

```

/dev/mmcblk0p1	/media/sd	auto	user,exec,rw			0	0

```

And here's what I got on dmesg for my working card and the two cards that don't work

```

[246217.464749] mmc0: new SDHC card at address 7f73
[246217.466355] mmcblk0: mmc0:7f73 SD04G 3932160KiB 
[246217.466755]  mmcblk0: p1
[246242.240132] mmc0: card 7f73 removed
[246267.275170] mmc0: new SD card at address 1234
[246267.276535] mmcblk0: mmc0:1234 SA02G 1927168KiB (ro)
[246267.285772]  mmcblk0: p1
[246289.736124] mmc0: card 1234 removed
[246339.929843] mmc0: new SD card at address 8fe4
[246339.932760] mmcblk0: mmc0:8fe4 SU02G 1931264KiB (ro)
[246339.933691]  mmcblk0: p1
[246351.372138] mmc0: card 8fe4 removed

```

In case you're wondering: card  7f73 is the working Kingston, card 1234 is the write-protected Kingston, and card 8fe4 is the SanDisk(also write-protected). Any attempts to writing or mkfs give me some error like "this filesystem is protected for writing", even if I do it as root. I also tried to change the user perissions to 777 after mounted, still no use.

Any ideas?

UPDATE: Also, it might work with an USB adapter, it has worked before... but since I have no USB adapter with me anymore, it's useless. I need a solution that works with my SD reader.

---

### Post by ram2500 on 2009-10-05
You couldn't write to the card at all through Vista as well? They come already formatted from the factory...You mentioned that you have a SanDisk card, so there is a utility that you can download from the SanDisk site that handles flash cards...I'm sure brands don't matter, so you will likely be able to use the utility with the Kingston card. This utility is only for Windows (unless they released one for Linux in a .deb format). This utility is like a Swiss Army knife for your flash cards and flash drives, so it can do formatting, handle folders, install programs to run off of flash drives and cards, etc.

---

### Post by niteshifter on 2009-10-05
> **guedesav said:**
> (Moved in here from "Laptop and Hardware" by the author)

This one that works is accessed through an SD adapter, and both others accuse protection, even though they're both new. I even tried them on Vista, but they can't be formatted either. [B]And, yes, I've checked the "Lock" switch on the adapter.
[/B]


Try another adapter, your's won't be the first one that has a switch / internal connections whose performance is marginal - I've had this happen to me: Some microSD cards report write protected, others didn't. Changed adapter, problem went away.

---

### Post by guedesav on 2009-10-05
I'm looking the site but can't find it. Also, my patience has run dry by now... could you link me there, please?

---

### Post by guedesav on 2009-10-05
> **niteshifter said:**
> Try another adapter, your's won't be the first one that has a switch / internal connections whose performance is marginal - I've had this happen to me: Some microSD cards report write protected, others didn't. Changed adapter, problem went away.

I have three adapters, no change. The one that works works in them all, and those who don't are still readonly in all of them.

---

### Post by guedesav on 2009-10-05
> **ram2500 said:**
> You couldn't write to the card at all through Vista as well? They come already formatted from the factory...You mentioned that you have a SanDisk card, so there is a utility that you can download from the SanDisk site that handles flash cards...I'm sure brands don't matter, so you will likely be able to use the utility with the Kingston card. This utility is only for Windows (unless they released one for Linux in a .deb format). This utility is like a Swiss Army knife for your flash cards and flash drives, so it can do formatting, handle folders, install programs to run off of flash drives and cards, etc.

I found one that recovers lost data, but can't fix a readonly disk... aw, damn it, I think I'll just have to buy a damn USB adapter and pray it works...

---


---
title: "Formatting microSD card error"
date: 2011-06-29
forum: General Help
---

### Post by SanzaBlancoAkA2C on 2011-06-29
I'm trying to format a SanDisk 16GB microSD card but when I do I keep getting the following message:
One or more partitions are busy on /dev/mmcblk0
So my question is how do I correct this so that I can properly format the card?  Any help is greatly appreciated.

Thanks

---

### Post by dcstar on 2011-06-30
> **SanzaBlancoAkA2C said:**
> I'm trying to format a SanDisk 16GB microSD card but when I do I keep getting the following message:
One or more partitions are busy on /dev/mmcblk0
So my question is how do I correct this so that I can properly format the card?  Any help is greatly appreciated.


Unmount all partitions in the device before formatting.

---

### Post by SanzaBlancoAkA2C on 2011-06-30
> **dcstar said:**
> Unmount all partitions in the device before formatting.

How exactly do I go about doing that because it won't let me do anything.  When I try to use the Disk Utility it won't allow for me to preform any task on it without error.

---

### Post by SanzaBlancoAkA2C on 2011-07-03
Any other ideas?

---

### Post by holadebob on 2011-07-04
Can you see it on GParted?

---

### Post by SanzaBlancoAkA2C on 2011-07-04
Haven't tried it.  I'm going to d/l it right now and see if I can fix this.

Thanks

---

### Post by SanzaBlancoAkA2C on 2011-07-04
Well it shows up in GParted and I've even begun to delete the partition but it's going on 2 hours and it hasn't even finished the first operation.  It seems to be doing something but I didn't think it would take this long for a 16GB microSD card.  Is this normal?

Thanks

---

### Post by wildmanne39 on 2011-07-04
> **SanzaBlancoAkA2C said:**
> Well it shows up in GParted and I've even begun to delete the partition but it's going on 2 hours and it hasn't even finished the first operation.  It seems to be doing something but I didn't think it would take this long for a 16GB microSD card.  Is this normal?

ThanksHi, I would not thinks so, but I have only reformatted disk drive and that does take a long time sometimes, it is possible that gparted is not responding, but I would hate for you to end the process to soon.

---

### Post by holadebob on 2011-07-04
I just formatted and partitioned my 16GB flash memory and it took about 30 seconds.

---

### Post by SanzaBlancoAkA2C on 2011-07-04
Here's the thing...it seems like its doing something because it has gone from step one to what I would imagine is the next step.  It went from calibrate to delete partition so I'm just going to let it be.  It's been running for 4+ hours on my System76 lumar with i3 processor so we'll see where this gets me.  I'll keep the post updated.

Thanks

---

### Post by SanzaBlancoAkA2C on 2011-07-04
6 and a half hours later and I'm no better than I was before.  GParted is stalling on the second step and I'm pretty sure its because of the same error.  I have no clue on what to do to fix this or what's causing it.  The card was used in my Nexus One Android phone before it became unreadable by the phone out of the blue.  The folders are still accessible when in my computer.  This really has me starching my head.

---

### Post by SanzaBlancoAkA2C on 2011-07-04
Here's a screen shot.  It basically just stays on that second stage.

---

### Post by wildmanne39 on 2011-07-05
> **SanzaBlancoAkA2C said:**
> Here's a screen shot.  It basically just stays on that second stage.
Hi, I think you have some bad sectors on the card and it is probably not going to finish.

---

### Post by SanzaBlancoAkA2C on 2011-07-05
Any idea on how to fix them?

---

### Post by holadebob on 2011-07-05
There's a utility called SCANDISK that can block access to bad areas. It's available for Windows. Make a run on Google for sd flash memory repair.

---

### Post by dcstar on 2011-07-05
> **SanzaBlancoAkA2C said:**
> Well it shows up in GParted and I've even begun to delete the partition but it's going on 2 hours and it hasn't even finished the first operation.  It seems to be doing something but I didn't think it would take this long for a 16GB microSD card.  Is this normal?

Thanks

Don't bother "deleting" anything, just use gparted to write a new partition table to the device.

---


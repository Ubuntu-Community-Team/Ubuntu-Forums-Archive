---
title: "Weird problem"
date: 2009-08-01
forum: General Help
---

### Post by sn0m on 2009-08-01
Hi Guys, turned computer on after the lates kernel update, and got this nice message:

[    9.804024] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[    9.804072] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[    9.804073]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[    9.804074]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[    9.804199] ata7.00: status: { DRDY }
[   14.844009] ata7: link is slow to respond, please be patient (ready=0)
[   19.828009] ata7: device not ready (errno=-16), forcing hardreset
[   19.828014] ata7: soft resetting link
[   19.992303] ata7: nv_mode_filter: 0x1f01f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[   20.008237] ata7.00: configured for UDMA/66
[   20.008516] ata7: EH complete
[   25.804023] ata7.00: limiting speed to UDMA/44:PIO4
[   25.804025] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   25.804070] ata7.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   25.804071]          cdb 12 00 00 00 60 00 00 00  00 00 00 00 00 00 00 00
[   25.804071]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   25.804196] ata7.00: status: { DRDY }
[   30.844009] ata7: link is slow to respond, please be patient (ready=0)
[   35.828009] ata7: device not ready (errno=-16), forcing hardreset
[   35.828013] ata7: soft resetting link
[   35.992302] ata7: nv_mode_filter: 0xf01f&0x1f01f->0xf01f, BIOS=0x1f000 (0xc50

I haven't got a clue where to start or what to do.
I'd appreciate some help.
Regards
Sokol

---

### Post by HermanAB on 2009-08-01
Howdy,

You just learned what I learned years ago already:  I do not update my production systems, I re-install them from scratch once a year. 

Auto-updates is a good idea for 'most people', but I have learned the hard way that my systems do not necessarily fall under that definition, which lead me to this truism:

In English: Leave well alone.
and in Amerikin: Don't fix it, if it ain't broke.

So, now that it is broke, WTF can you do???

I would boot with a CDROM (Ubuntu or Knoppix) and try to read the data.  If you can, copy all data off to another disk and then re-install from scratch.  Then, turn off the gawddamm automatic fsck-up feature, unless you want it to happen again.

BTW, when I build a single system for a client e.g. a laptop machine, I enable the auto-updates, cross my fingers and hope for the best, but when I build a file server for that same client, I turn the auto updates off and leave the machine pretty much alone for one to five years.

Hope that helps!

---

### Post by RD1 on 2009-08-01
Uh ... press "esc" at Grub and boot with the old kernel? ;)

---

### Post by Bucky Ball on 2009-08-01
Yep, go with the last kernel for now and try the new one periodically. You may find it gets fixed in the next few updates.

(ps: Jaunty (testing) is definitely NOT something I would dream of running on a production machine. Glitches like this are to be expected - nature of the beast - and to be overcome! That is why people test, so snOm, don't be too shocked. Try something that has been around awhile like 8.04 LTS if you are looking for the most stable at the moment.)

:)

---

### Post by hyperAura on 2009-08-01
so the whole problem was caused by an update which happened to cause a bug in the kernel??

---

### Post by prshah on 2009-08-01
> **sn0m said:**
> 
[    9.804024] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen


It has nothing to do with the kernel update.

You have some damage to the hard disk drive, usually logical, rarely physical. You can set it right by running a simple fsck. Give the following command in a terminal (Applications-Accessories-Terminal)```
sudo touch /forcefsck
``` and reboot normally. A disk check will be triggered, and any underlying problem automatically (hopefully) repaired.

---

### Post by alicia8522 on 2009-08-01
HermanAB is right. I also learned it the hard way. Avoid installing updates.

---

### Post by sn0m on 2009-09-03
Hi chaps, if anybody is interested I managed to find out that the reason behind it was a faulty cd/dvdrw drive. What a headache but is all sorted now.
I hope this helps anyone that comes across it.
Thanks for all your thoughts
Sokol

---


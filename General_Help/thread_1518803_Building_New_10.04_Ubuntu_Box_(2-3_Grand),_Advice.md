---
title: "Building New 10.04 Ubuntu Box (2-3 Grand), Advice?"
date: 2010-06-27
forum: General Help
---

### Post by vintagedon on 2010-06-27
After a couple of years, I am returning to Ubuntu as my primary OS.  For this, I am building a new system (I have a beast of a Windows desktop, but retiring that as an HTPC and building a new desktop).  Will be moving some items from the Windows desktop like the speakers, keyboard/mouse, monitors, etc, that will not serve with the HTPC configuration.  Have a couple of grand put aside, and am just looking for a few pieces of advice.

Basically, this is what I am building (amost identical to my current Windows machine, except it's a Core2Quad and has 12GB of RAM):


[LIST]
[*]i7-860
[*]P55 chipset motherboard
[*]8GB of RAM
[*]system/boot volume volume 2x64GB 2nd gen 64GB SSDs in RAID0 (have hardware garbage collection so will run find in RAID)
[*]data volume 6x1TB SATA in RAID5
[*]3 x 21.5" 1920x1080 monitors on a triple monitor stand (from Win desktop)
[*]2 x 1TB and 2 x 2TB Fantom Green Drive External eSATA drives (used for backup; from Win desktop)
[*]Logitech z5500 speakers (from Win desktop)
[*]RocketRaid 2320 8-port SATA RAID card
[*]Saitek Cyborg Keyboard, Logitech G5, Belkin n52te gamepad
[*]Microsoft LifeCam
[*]HT Omega Striker 7.1 sound card
[/LIST]

That's the basic system I'm building.  My questions:

**Video Card:** with 10.04, should I go with ATI or nVidia for a card?  Am running triple monitors, and will be gaming using Cross-Games and Cedega.  Which drivers between the two manufacturers is performing the best and would be best for gaming/multiple monitors.

**RAID Card:** The 2320 says it has native support in the 2.6.25 kernel.  I get good speeds (500-600 MB/sec on both the SSDs and the RAID5) and no troubles with it on the Win Desktop.  Should I have any issues with it under 10.04 or would there be a suggestion in the <$350 price range to replace it with?  Or, would running the ICH10R off the motherboard work with the alternate CD?

**SSD Setup: **What partitions would be best to keep off the SSD volume and on the RAID5?  I know /tmp, /home, /var, and /swap should be kept off the SSDs to reduce the excessive writes.  Any other suggestions?  With a 128GB system/boot volume, what would you do for partition sizes there?

**Sound Card:** Is the Omega supported under 10.04?  Or another suggestion for good 7.1 surround sound?

Anyway, 1/2 of the new box is here already the rest is on the way, and waiting on a few items to see what happens in this thread.  Would appreciate any of the Linux box building heads out there that decide to drop by and give some good advice.

Thanks :)

As Always,
VintageDon

---

### Post by Leppie on 2010-06-27
no much, but:
> **vintagedon said:**
> Or, would running the ICH10R off the motherboard work with the alternate CD?
never use the onboard raid (fake raid) functionality, it will cause you more sorrow than happiness. software raid is working pretty well.

---

### Post by vintagedon on 2010-06-27
Yep, have heard the same about FakeRAID, although several of my friends have been running it for a number of years with no issues.

Appreciate the input.

As Always,
VintageDon

---

### Post by Helios747 on 2010-06-27
ATI simply because they give a better performance to price. And the Linux drivers are actually pretty decent now.


Also, hot ****ing damn at your budget. Nice!

---

### Post by vintagedon on 2010-06-27
Helios:

Thanks: I am definitely an ATI guy when it comes to graphics (running dual 4870x2s on the Win desktop), but I knew that a couple of years ago, the ATI drivers were not up to the bar they needed to be (one of the reasons I went back to Win).

Anyway, as far as the budget, I usually get a new desktop every 12-18 months, and I always put back $150-$200 a month towards that, so that when I'm ready to get my new box, I have enough that I can stay where I like to be.

Thanks for all the input everyone.  Anyone else want to chip in on the other areas/questions?

As Always,
VintageDon

---

### Post by vintagedon on 2010-07-13
All right, all parts are in, now I'm doing the OCD thing about my partitions.  Basically, I'll have two distinct volumes: 128GB (2 x 64GB SSDs in RAID0) and 12TB (8 x 2TB in RAID6).  Was thinking maybe a gig or so for boot on the SSDs, and the rest to /usr with everything else on the RAID6 volume.

Obviously, I want the stuff needing the quickest access on the SSD, but nothing that would grind in there, like /var/log ...

Anyone want to weigh in on this and perhaps give me some partitioning setups as a guide?

Thanks in advance :)

As Always,
Vintage Don

---


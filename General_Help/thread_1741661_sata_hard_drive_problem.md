---
title: "sata hard drive problem"
date: 2011-04-28
forum: General Help
---

### Post by Benbow on 2011-04-28
I have 2 SATA 1tb hard drives, one with win 7 plus ubuntu 10.10 and the other I use to keep my Humax programmes on (no operating system).
The first failed last night - I had turned it off and later restared it but it was dead. I used my copy of ubuntu to boot up the pc which was fine but no hard drive!!
This morning I tried it in my docking station with my TV but it was still dead.
I then tried the second h/drive (no operating system) in my pc and it wouldn't see it.
I have also just tried the 2nd hd using my docking station via usb on my wife's laptop and it recognises it but can't read it.
As a test, I have tried an old IDE drive on my wife's laptop with no problems.
This seeems like a SATA problem of some sort, any ideas? 
Brian

---

### Post by dino99 on 2011-04-28
then look at bios settings: try ahci or better "compatible" if available

if you can run testdisk on your failed hdd, maybe it can resolve that issue

---

### Post by wizard10000 on 2011-04-28
I don't think this is a disk failure.

Some motherboards have more than one SATA controller - you might try that.  At the very least I'd try all ports.

A cheap SATA card is less expensive than a new motherboard  :)

---

### Post by Benbow on 2011-04-28
Thanks Wizard & Dino.
[I]Some motherboards have more than one SATA controller - you might try that. At the very least I'd try all ports.
[/I]
Could you point me in the direction of some help here, Wizard, my technical brain cells are a bit stretched here.  The calamity happened very quickly and it does seem like a hardware failure

[I]then look at bios settings: try ahci or better "compatible" if available
if you can run testdisk on your failed hdd, maybe it can resolve that issue 
[/I]
I am unable to access the hdd, dino, it won't respond to anything. I would try ahci but I have looked at it on the net and it is a bit beyond my abilities, I think.

Thanks, Brian

---

### Post by wizard10000 on 2011-04-28
> **Benbow said:**
> Could you point me in the direction of some help here, Wizard, my technical brain cells are a bit stretched here.  The calamity happened very quickly and it does seem like a hardware failure

I've had a single SATA port die and the rest of them worked fine.  If you've got more internal SATA ports try plugging the hard drive's data cable into a different port.  It might work, it might not.

Unless your PC got hit by a power spike or your power supply failed in a rather odd way the chances of two hard drives dying at the same time are really, really slim.  I suspect the SATA controller - but as I mentioned above it might be that just one port died.

Another thing you might try before you buy any hardware is to reset the CMOS on the machine.  Most motherboards have a BIOS reset jumper - you put a jumper on the terminals and power on the machine for a second to clear the CMOS.  If your motherboard doesn't have a reset jumper just take the battery out of the motherboard and leave the machine powered off overnight.

---


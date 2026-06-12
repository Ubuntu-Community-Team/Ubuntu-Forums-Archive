---
title: "New hard drive problems"
date: 2009-06-26
forum: General Help
---

### Post by drummerchrissk on 2009-06-26
I need major help. I just bought a Western Digital Scorpio Blue, 250 GB, IDE drive for my Compaq Armada E500. I put it in and I turn my computer on. I see my two normal boot screens and then get a screen that says...

> Intel UNDI, PXE-2.0 (build 071)
> Copyright (C) 1997,1998,1999 Intel Corporation

This does not alarm me at all. If I am wrong in this, please let me know.

What alarms me is this...

> PXE-E61: Media test failure, check cable

This appears a few seconds after the other text. If my system were to boot my Live CD after this, I wouldn't be worried. However, after only a few seconds, my screen flashes several times (seven by my count), and brings me to a fresh screen with this....

> Non-system disk or disk error
> replace and strike any key when ready

I hit a key, and my screen flashes several times again and shows this text over and over and over.

I just spent close to $100 for this thing. I really hope there's an easy fix.  I've checked and rechecked my connections. I am at a loss.

PLEASE HELP!!!!

---

### Post by QIII on 2009-06-26
Let me get this right...

You had one disk that you took out, and you installed a new disk?

Your BIOS is set to boot first from the CD drive?

---

### Post by drummerchrissk on 2009-06-26
The computer originally came with a 12 GB hard drive. I switched it a few years back for a 20 GB drive. Now that drive is starting to fail on me, so I went out and bought this new one.

Upon further reading I have discovered that the "Non-system disk or disk error" message is received because the system cannot find boot files. In other words, there is no OS on the system. However, I have a Windows XP CD in the disk drive, so what am I doing wrong. (I plan on dual booting)

---

### Post by QIII on 2009-06-26
You're losing me.

Are you able to boot from the XP CD -- an XP install CD?

Again -- Is your bios set to boot first from the CD drive?

---

### Post by drummerchrissk on 2009-06-26
No, I am not. It is in the drive and I can hear the disk spinning but I am getting no results. I believe in my BIOS that the CD ROM drive is labeled as a "Multibay" or something like that. I had that booting first in my boot options, but changed it after the first few attempts at this. Now my hard drive boots first. That is not going to get me anywhere.

---

### Post by QIII on 2009-06-26
Set your BIOS back to boot from CD first.

Are you using SATA drives, or IDE drives on the 0 and 1 terminals?

If you are using SATA drives, which one is on the lowest numbered header on your motherboard?  WARNING -- if you want to swap them, don't ever unplug the cables from the motherboard side.  SATA headers have a bad habit of coming off the motherboard with the cables, and if you bend or break a pin when that happens you are SOL.  Once a SATA drive is connected to the motherboard, I always recommend that you disconnect them on the drive side.

If you are using IDE drives, are they set so that the drive on the 0 terminal is master and the one on the 1 terminal is slave?

---

### Post by drummerchrissk on 2009-06-26
I am using an IDE drive, but this talk of terminals has got me lost. : P

Sorry, I've learned a lot about computers very recently, but I have not come across that yet.

---

### Post by drummerchrissk on 2009-06-26
I'm going to try this again. I will return if it still does not work.

---

### Post by QIII on 2009-06-26
OK.  First thing is to set your BIOS back to boot from CD and shut down.

This is going to be a little difficult to explain.  It would be better to cart the machine to a computer shop, pay $20 and have someone sort this out.

But I'll try.

Unplug your machine and open the case back up.

Look at the wide IDE cable coming off your motherboard (NOT the floppy drive cable).  There are probably two white, gray or black plastic plugs on the end you plug into your disks.  One one side of the cable, on the cable itself, not the plugs, there should be two stamped numbers.  0 and 1.

The 0 terminal is usually the one on the very end of the cable.  The 1 terminal is usually a couple of inches back toward the motherboard.

Keep that in mind.

Now, you may have to take your drives out.  On the backs of the drives there will be one recepticle for the IDE cable and one for the power cable.  There will also be a series of pins with a jumper between a couple of them.  On the disk itself somewhere, you will have a hard-to-understand chart of how to set that jumper.  Your choices will typically be Master, Slave and System Select.

FIRST we want to get you back to a point where you can get back into XP so we can start from there.  Someone else will have to talk you through the rest of this, since I have to go to bed now, work tomorrow and drink a lot of beer tomorrow night.  OK, maybe milk.  I'm a little old for the late night drinking.

I am assuming that you have already backed up anything you wanted from the old drive, so set it aside.

Figure out the jumper configuration to make the NEW drive Master (again -- this is assuming you have an IDE drive -- one with a gray cable and not a 3/4 inch wide red, blue, purple, neon cable with black ends.  That is a SATA cable, and we are barking up the wrong tree.)

Plug the 0 terminal into the back of the drive, plug the drive power cable in and put the drive in the bay.  Screw it down.

IF you have your BIOS set to boot from CD, you will now have a system that can boot from CD and has a very empty drive on which to install XP.

The reason I'm having you do it this way is that dual booting on a single drive is MUCH easier if Windows is installed first.

I'm off to bed.

Someone on the other side of the Date Line can help from here if you don't get anywhere.

Good luck.  I'll try to check in again tomorrow.

---

### Post by drummerchrissk on 2009-06-26
Thank you for your help. I will keep your post in mind, but instead of all these cables, there is a small piece that connects to the pins on the drive and from there the drive, for better lack of words, slides into place. I have no clue if you know what I mean. : P

I'm hoping that maybe I can just figure this thing out with Ubuntu installed first. I could always use the knowledge of learning to partition a drive. : P

I don't know yet. I will hopefully figure something out. I'm going to fiddle with it for a bit. I will check this thread again before I go to bed. ANYBODY with ANY sort of advice here would be MUCH appreciated.

Thanks again QIII!

---


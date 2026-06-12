---
title: "Laptop will not boot"
date: 2009-07-20
forum: General Help
---

### Post by Eamon1 on 2009-07-20
Hi,

I was using my laptop today and noticed firefox going a little slowly, and excessive hard drive activity. Firefox crashed, then claws mail crashed, gnome-power-manager seemed confused (the tray icon appeared and changed to a white box with a red cross and told me my laptop was charging even though it was plugged in about 15min previously), VLC crashed,... . Everything seemed to be dying so I attempted to log out (unsuccessfully).

I restarted and noticed something peculiar, I had turned off the splash screen that appears when the computer is fisrt turned on (it shows the brand of the copmtuer while the BIOS does its thing) some time ago, but it appeared this time. The progess bar stopped before I got to GRUB. There was an option to press escape for "Diagnostic Screen", so I try that and all I get is:

```

Phoenix TrusterCore(tm) NB
Copyright 1985-2004 Phoenix Technologies Ltd.
All Rights Reserved

BIOS version D3C72
System ID =  70401296
Build Time: 12/22/06

1 Processors Detected, Cores per Processor = 2
CPU = Intel(R) Core(TM)2 CPU T5500 @ 1.66GHz
1015M System RAM Passed
2048K Cache SRAM Passed
System BIOS shadowed
Video BIOS shadowed



Press <F2> to enter SETUP

```

Everything stops here (although I would note the hard drive light is on all the time).

If I press F2 the last line changes to "Entering SETUP ..." and nothing else happens.

I don't know if this could be related, but I've been having some issues with extremely slow boot times recently. Occasionally (about 1/3 of the time when I turn my laptop on) the RAM test takes a long time (maybe 3+ minutes) but everything works ok if I leave it long enough.


Sorry for the long question, but in summary, my laptop won't boot and I have no idea where to even begin to look. So does anyone have any ideas where the problem may be?

If it helps, more info about my laptop is at [http://www.uktsupport.co.uk/advent/laptop/qt5500.htm](http://www.uktsupport.co.uk/advent/laptop/qt5500.htm) and I am using Crunchbang 9.04 (based on Jaunty)  (dual boot with Vista but it hasn't been used in months)

Thanks

(I should also say I've posted this over at Crunchbang forums [http://crunchbanglinux.org/forums/topic/3635/laptop-will-not-boot/](http://crunchbanglinux.org/forums/topic/3635/laptop-will-not-boot/) but so far have had no response so I thought I'd see if anyone here has any idea)

---

### Post by t4thfavor on 2009-07-20
Unplug it, and take out the batteries for a few minutes, try it then. If you still get the same error, you will need to find where the CMOS battery lives, and repeat the process with that battery removed as well.

If you still have problems, I would try testing with only one stick of ram in, then the other. Though its quite possible that you will fix this with the first procedure.

---

### Post by Eamon1 on 2009-07-20
Hi, thanks for the help.

I've tried removing batttery/unplug etc. with no result.

I'll try CMOS battery and RAM now.

---

### Post by ddrichardson on 2009-07-20
Try disconnecting the hard drive and see if it will let you into BIOS.

---

### Post by Eamon1 on 2009-07-20
I tried the RAM one at a time, still not working.

After a thourough search I am still unable to locate the CMOS battery. Theres only small doors on the bottom of the laptop and seems near impossible to get the whole case apart.

I'll have a go at the hard drive now though, see if I can get anywhere.

Thanks again.

---

### Post by Eamon1 on 2009-07-20
OK, I've just tried it without the hard drive.

After the screen above, I get:

```

Yukon PXE v5.0.2.3 (20060127)
(C)Copyright 2003-2006 Marvell(R). All rights reserved.
Pre-boot eXecution Environment (PXE) v2.1
(C)Copyright 1997-2000 Intel Corporation.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Operating System not found
_

```

Pressing any key refreshes the screen.

Any more ideas?

---

### Post by ddrichardson on 2009-07-20
Yes, without a drive there's no OS, the media rest ailure is the drive not being there - this is likely to be the cause of the previous hanging.  Does it boot into BIOS at a normal speed without the drive fitted?  If so then the drive is U/S.

---

### Post by Eamon1 on 2009-07-20
Thanks for the reply.

Yes it does boot into the BIOS at normal speed without the hard drive.

Also, without the hard drive I can now access the BIOS settings, i.e. it no longer hangs when pressing F2.

Sorry for being an idiot, but what do you mean by U/S?

---

### Post by Eamon1 on 2009-07-20
Hi again,

I've just tried it with no hard drive and with a live cd and it seems to be working  ok.

I guess this means I'll need to go shopping for a new hdd?

---

### Post by ddrichardson on 2009-07-20
> **Eamon1 said:**
> Sorry for being an idiot, but what do you mean by U/S?
Sorry Un-Serviceable. Yes it would seem you hard disk is done for.  They're often located badly on laptops and are prone to overheating, especially if left on carpets/bedspreads etc,

---

### Post by Eamon1 on 2009-07-20
Yea, it does get pretty hot, so its not surprising really.

Thanks again for all the help.

Just one more (idiotic) question:

In the manual for the laptop in the specs it says:

"Hard Disk Drive:  Supported capacities of 40/60/80/100 GB" 

So does this mean that the manufacturer will only support those capacities or it will only work with those capacities? As far as I know you can put any size in there and it will work just fine. Am I wrong?

Anyway, its not all bad, I was considering getting a bigger hard drive anyway, now I've got a pretty good excuse!

---

### Post by ddrichardson on 2009-07-20
I don't know to be honest, there might be some limitation in the controller but I suspect they just made the laptop in those capacities.

---


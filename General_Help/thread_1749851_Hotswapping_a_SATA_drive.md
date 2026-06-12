---
title: "Hotswapping a SATA drive"
date: 2011-05-04
forum: General Help
---

### Post by dnoyeb on 2011-05-04
I have a SATA drive, and a hotswap bay on my case.  I am trying to hotswap this drive.  It does not seem to work.  If I restart the computer I see the drive, and I see the other drives shifted.  If I restart without the drive, I see the other drives shifted back.

adding or removing the drive while the computer is running does not seem to have any effect.

What am I missing?

---

### Post by Hedgehog1 on 2011-05-05
* Your SATA controller must support hot swapping
* You need to 'unmount' the drive before you remove it, and 'mount' the new drive after you have inserted it.

If your controller does not support hot swapping (and few do outside of a raid configuration), then change the drive when power is off you your only reliable option.


***The Hedge***

:KS

---

### Post by dnoyeb on 2011-05-05
How do I know if my MB supports hot swapping?  Its a fairly recent board but it was on the cheap side since its only serving up files.  I even had to buy a GB network card for it.

I tried searching newegg to see if I could find boards that supported hot swapping, but none seem to mention it.

Thanks.

---

### Post by phazei on 2011-05-07
Just build me a new system and had the same question.  Did you get the Antec Two Hundred case?

If you want to be able to hot swap any SATA drive, you have to be using "AHCI" mode, not Native IDE mode.  You can change that setting somewhere in your BIOS.

AHCI enables hot swapping and native command queuing.  I didn't have an issue with it.  I just took my old hdd with ubuntu out of my dead laptop and booted it in my new desktop.  Had small issue with the video driver, but all else went pretty well.  Usually AHCI needs extra drivers, but I guess they are built into ubuntu, at least 10.10+

---

### Post by dnoyeb on 2011-05-09
Hmm, OK.  I don't see an AHCI option in my BIOS.  I guess that means it does not support hot swapping.  No matter, after adding a 2nd drive to complete my SW RAID, I don't have any more ports :)

So I need to use my USB hot swap drive thing anyway...

thanks for the help.

---


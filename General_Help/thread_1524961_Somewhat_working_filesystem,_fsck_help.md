---
title: "Somewhat working filesystem, fsck help"
date: 2010-07-06
forum: General Help
---

### Post by Nickemans on 2010-07-06
Hey guys, thanks for reading.

After trying to install a package through synaptic, my computer froze and I forced it to shutdown.
Since this, it keeps running "fsck from util-linux-ng 2.16" but it takes at least a few minutes before it finally ends up at the login screen.
I keep seeing errors like "ata1.00: status { DRDY ERR }" and "ata1.00: error { UNC }" and I have no idea what these mean.

Have been searching through the forum for similar problems and have tried using fsck and e2fsck through the liveCD and it seems like it should have fixed the errors, but when I reboot, nothing's changed.

If anyone can help me out, that would be very much appreciated.

I run Ubuntu Karmic Koala btw.

---

### Post by Nickemans on 2010-07-27
Bump.

I recently tried the Live CD again, and had a look at GParted. Apparently there is a problem with my swap partition. It shows up as of type "Unknown" and it does not say how much space on it is used.
Has anyone had this problem before or knows how I can solve this? I would really appreciate it!

---

### Post by iponeverything on 2010-07-28
I'd run fsck with the badblocks check.

Use synaptic to install:

GSmartControl
smartmontools

You can then to:

Applications -> System tools -> GSmartControl 

to see if the disk is reporting errors.

---

### Post by Nickemans on 2010-07-30
I tried the above, and I saved the log the program gave me.
I have no idea what it means however, heh...

I've attached the file here:

---

### Post by iponeverything on 2010-07-31
It looks like your drive has issues.


Open the GUI for tool under:
 
Applications -> System Tools -> GSmartControl 

and see if it is kind enough to flag serious errors for you.

---

### Post by Nickemans on 2010-07-31
Where would I find these errors?
Annnd also, depending on whether I find errors or not, is there any way to fix it?

Cheers

---

### Post by iponeverything on 2010-07-31
humm...

open the tool and look around. 

Do you see the icons of the hard drive? 

highlight it (click on with your mouse)

See the "Device" menu at the top? Go to it and click on "View Details"

There you will see several tabs, which I hope are fairly self explanatory.

If your drive has issues, replace it. Either through warranty or just buying a new one. Smart is to help warn of errors before your drives fails, so that you can do something about it.

---

### Post by Nickemans on 2010-08-29
Sorry it's been a while! I've been crazy busy T_T

Anyways, I had another look at the GSmartControl program, and it says my HDD 'passed' the test...

I'm guessing the problem is the swap partition, but I'm not sure if I can delete it; will that cause problems? I'm quite ok with losing my ubuntu partition as I have all the important stuff backed up anyway, so if anyone can shed some light on this, that'd be great!

Thanks

---


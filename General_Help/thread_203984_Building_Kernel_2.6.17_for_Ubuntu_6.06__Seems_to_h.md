---
title: "Building Kernel 2.6.17 for Ubuntu 6.06?  Seems to hang on boot..."
date: 2006-06-26
forum: General Help
---

### Post by gmcgraw0 on 2006-06-26
I am running Ubuntu linux 6.06 on a Toshiba Portege R100 laptop and I just built a slightly patched 2.6.17 Ubuntu kernel. When I tried booting it, it gets stuck as it is waiting for the main root partition to mount ("Waiting for root file system...").  After about 10-20 minutes, it fails and takes me to an "Ash" shell where I have the option of entering commands (the kernel does not crash).  First of all, I am wondering if many people do this regularly (run a recent kernel on Ubuntu stable) and second of all, I was wondering what steps I might take to troubleshoot.  The patches that I applied are supposed to enable better SD (secure digital) card support for linux (apparently specs were recently released that allowed developers to better support the common SD card slots).  I do not think that this patch was is the cause of the kernel not booting (the patch only modified a few driver related files).  Therefore, I am left to believe that something is wrong with how I built, setup, or installed the kernel.  I used the "rules" install script to build and I built for the 686 chipset.  Currently, I am running the 2.6.15 kernel with no problems whatsoever so I am puzzled to experience problems with a kernel that is only two subversions away.

Thanks in advance for any suggestions or tips.  Let me know if there is any extra information that I can provide that might help.

-Garret

---

### Post by gmcgraw0 on 2006-07-07
I checked the messages as ubuntu boots in safe mode (or whatever the alternate mode is called) and saw that it was seeing my drive as sda instead of hda.... weird! (isn't sda only for SCSI drives?  I don't think that I have a SCSI drive...)  Anybody know why?  But anyway, I changed the root boot parameter to sda2 and it boots fine.  When it finally comes up, my root partition is back to being mounted as hda2!!! soooo, that's weird, why did it change back after the finally booting?!  I still must boot into sda2 to get it to boot at all... even though it ends up being hda2.  If anybody knows why this is, I would love to know!

-Garret

---

### Post by PriceChild on 2006-07-07
Kernel compiles don't always work perfectly,

I regularly find that simply loading to a previous kernel and trying it all again works the next time :)

---

### Post by Rui Pais on 2006-07-07
hi,
can you give more info on how you make your .config file? do you used make oldconfig? 

How do you make your filesystem drivers? ext3 or others, as modules or build-in? and ide and scsi (and/or related ones like sr_mod) are build-in? are modules?

What the output of lsmod with the 2.6.17 kernel?

I agreed that 2.6.15 are old.  But, may i suggest, that you try to build a 2.6.16. The .17 series are new and add a lost of new things (some very promissing), but seems that it's yet a litle in the land on unstable, not well tested, kernels :(... 
I always build my kernels (and btw i never notest any bizarre behavier as PriceChild described), but i never got a 2.6.17 running perfectly and smooth as .16 series. And when it cames to patchs, then it's a certain that most of them are still trying to stabilized on .17...

---

### Post by rbmorse on 2006-07-07
My SATA (Serial ATA) drives show up as SCSI devices in Dapper, but theit designations don't change (i.e., sda2 stays sda2).

---

### Post by Hezekiah on 2006-07-07
I remember seeing something about ATA drives showing up as SCSI after moving to 2.6.17 a few days ago - it may just be a kernel bug, or an imcompatibility between something in Dapper-vs-Edgy outside of the kernel.

Perhaps it would be worth taking a look at Launchpad if you're using a manually backported Kernel from Edgy.

---


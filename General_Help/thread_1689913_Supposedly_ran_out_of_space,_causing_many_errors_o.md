---
title: "Supposedly ran out of space, causing many errors on next boot and loss of settings"
date: 2011-02-17
forum: General Help
---

### Post by reign1 on 2011-02-17
Well recently I booted up 10.10 to be faced with many errors about every app you can think of due to apparently having 0 bytes left on the drive. The filesystem was reported to have about 100GB more data than the partition is even capable of holding...

This, of course, was not the case. In actuality, I had 4GB free.

All of my AWN icons were gone and my terminal color profile was reset, and I'm sure some other settings were reset as well. Starting any program resulted in an xauthorization error, and many dialogs about reporting bugs to launchpad were popping up.

On a subsequent reboot after clearing /tmp, I did not get any errors but my settings were still at their defaults.

I reconfigured the programs that appeared to have lost their settings and things seem back to normal, and the filesystem is correctly recognized as having 4gb of free space again, but should I be worried?

I believe this occured after a lockup in which my drive was clicking. This is the first time this has happened and smartmon utils report a healthy drive and memtest has no errors after 5 passes.

I'm inclined to think the hardware is fine, but what could cause this sudden misreporting of how much space was free on the drive? I'm worried things have broke behind the scenes and this install is a ticking time-bomb now... 

Any ideas?

---

### Post by blueridgedog on 2011-02-17
How big is the partition?  The "root" user is reserved 5% by default, so you may run out of space sooner than you think as that can add up to significant space (if you have 100GB, that is 5 gig).  You can reduce the root reservation with tune2fs.

---

### Post by reign1 on 2011-02-17
Thanks for the response. Partition was only 18gb.

---


---
title: "Natty freezes completely when left for a while!"
date: 2011-05-13
forum: General Help
---

### Post by mov on 2011-05-13
I just upgraded from 10.10 to 11.04 (64bit) and it seemed fine for a few days, then the machine started freezing completely if left for a while (haven't had it freeze while I'm using it...).

It seems to be completely unresponsive, although I'll have to try Sysrq next time it happens.

I've run memtest86 all night, run HDD diagnostics, removed my wireless card, swapped out the graphics card (7900GS -> 7600GT), downgraded the graphics driver, played with ACPI settings in the BIOS, etc.

Any suggestions from anyone as to how to try and debug this?

Hardware specs: Desktop machine, A8N-SLI, 2gigs of PC3200, a Promise ATA controller card with a couple of 200gig Seagates attached, single-core Athlon64 3500+, Creative SBLive! sound card, couple of IDE optical drives and a decent PSU.

It's driving me nuts. :( The weird thing is, as I mentioned, it was fine for a few days after the upgrade to Natty (IIRC, the only updates I did pertained to CUPS).

BTW, I never had any problems like this with Lucid or Maverick.

Help me!

---

### Post by carl4926 on 2011-05-13
Try disabling the screensaver if you have it enabled

---

### Post by mov on 2011-05-15
The problem seems to be fixed.

The only things I've done since are to swap out the graphics card and to update the kernel to 2.6.39-0 via kernel-ppa.

I'm guessing it's the new kernel that fixed it, but will put the 7900GS back in to verify.

---


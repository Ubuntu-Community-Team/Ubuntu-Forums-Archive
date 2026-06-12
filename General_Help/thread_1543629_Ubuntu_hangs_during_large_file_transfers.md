---
title: "Ubuntu hangs during large file transfers"
date: 2010-08-01
forum: General Help
---

### Post by Headcase_Fargone on 2010-08-01
I recently built a home media server and decided on Ubuntu 10.04.  Everything is running well except when I try to transfer my media collection from other PCs where it's backed up to the new machine.

Here's my build and various situations:

Intel D945GSEJT w/ Atom N270 CPU
2GB DDR2 SO-DIMM (this board uses laptop chipset)
External 60W AC adapter in lieu of internal PSU
133x CompactFlash -> IDE adapter for OS installation
2(x) Samsung EcoGreen 5400rpm 1.5TB HDDs formatted for Ext4

Situation 1:
Transferring 200+GB of files from an old P4-based system over gigabit LAN.  Files transferred at 20MBps (megabytes, so there's no confusion).  Took all night but the files got there with no problem.  I thought the speed was a little slow, but didn't know what to expect from this new, low-power machine.

Situation 2:
Transferring ~500GB of videos from a modern gaming rig (i7, 6GB of RAM, running Windows7, etc etc).  These files transfer at 70MBps.  I was quite impressed with the speed, but after about 30-45 minutes I came back to find that Ubuntu had hung completely.

I try again.  Same thing.  Ubuntu hangs after a few minutes of transferring at this speed.  It seems completely random.  I've taken to transferring a few folders at a time (10GB or so) and so far it has hung once and been fine the other three times.

Now, I have my network MTU set from automatic to 9000.  Could this cause Ubuntu to hang like this?  When I say hang I mean it freezes completely requiring a reboot.  The cursor stops blinking in a text field, the mouse is no longer responsive, etc.

Any ideas what might cause this?

---

### Post by llamabr on 2010-08-01
Weird.  What are you using to xfer the files?  Drag and drop, or cli?  

If the former, try the latter.  If the latter, what protocol?  And what command?

I'm not sure how to trouble shoot it, but I suspect that doing it differently will either 1. work, or 2. give some insight into the problem.

---

### Post by Headcase_Fargone on 2010-08-01
I'm dragging and dropping on the Windows machine to a Samba share on the new one.  I forgot to mention that the machine that the transfers worked on (albeit slowly) was also running Ubuntu 10.04.

I'm unsure of what cli is since I'm new to Linux in general, but I'll go research it right now.  Thanks.

---

### Post by Headcase_Fargone on 2010-08-01
Update: It may have been as simple as overheating.  This is a tiny mini-ITX case with but a single 80mm fan that doesn't move much air.  I took the side of the case off and have transferred over 300GB of files (piecemeal, but still) in the past couple of hours and no locks.

Since I'm posting this it will of course probably hang any second after hitting submit...

---

### Post by llamabr on 2010-08-02
good one.

Also, rather than relying on the drag/drop, wget will let you continue a disrupted transfer, with the -c option.

---


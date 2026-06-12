---
title: "ScanJet 6200c Causes Boot-Loop"
date: 2011-02-16
forum: General Help
---

### Post by jamesisin on 2011-02-16
I have a system which has been running 8.10 for two years (and am preparing to rebuild, thanks). Yesterday I thought to reboot it and am now stuck in a boot-loop getting the "not responding" x.xxxxxx error.

I made no changes prior to the reboot (just felt it was time) other than moving documents off the main drive onto a spare (preparing for the rebuild).

I have tried booting into several of the previous kernels and I ran memtest (flying colors). I keep getting the same error.

I have now built a 10.04 system for this machine.  The old 8.10 drive seems to be in perfect order and I was able to pull various files from it.

I thought this would be the end of it but if I boot this new machine with my HP scanner attached via USB (any port) I get the boot-loop as in 8.10.

Again no changes were made to the 8.10 build prior to yesterday's reboot, and that scanner has been attached for more than two years (and working with fair reliability).  I have had to alter its USB port or (inclusive) power-cycle it for Ubuntu to find it, but I had to do this when it was attached to an XP machine and so thought nothing of it.

Why has (presumably) the kernel driver suddenly crapped its pants?

Oh, and for the doubters I was able to boot into 10.04, open x-sane (which I prefer over Simple), locate the scanner (after power-cycling it), and scan an image.  I just had to attach the scanner to the machine after the kernel loaded (at the login screen).

---

### Post by jamesisin on 2011-02-17
Any ideas?  The new build has now (successfully? randomly?) rebooted with the USB scanner attached.  I do have this work-around, but I'd rather understand the problem (and perhaps even solve it).

---

### Post by jamesisin on 2011-02-22
I don't know how I manage to come up with these impossible to decipher issues.  Nobody has any insight?

---


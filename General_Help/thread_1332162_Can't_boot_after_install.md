---
title: "Can't boot after install"
date: 2009-11-20
forum: General Help
---

### Post by hessian on 2009-11-20
I just installed Ubuntu 9.10 side by side with Windows XP. Now whenever I try to boot my computer, the boot process never finishes.  It gets to "GRUB loading." with a blinking underscore, then never gets past this step.  I've searched for this error, but only found ones where an error message returned, not the problem I am currently having where it just hangs.

I'm not very experienced with linux so detailed instructions would be a huge help!  Everything worked fine before installing, and Hard drive diagnostics have found no errors.  I'm running on a 2.2 GHz core 2 duo.

When I try launching the install a second time, I some I/O errors:  
Removing gdm-guest-session ...
[124.313337] end_request: I/O error, dev sr0, sector 1413124
[124.313382] Buffer I/O error on device sr0, logical block 353281

Any help is much appreciated! thanks!

Mike

---

### Post by hessian on 2009-11-20
Nevermind, fixed my issue.  I had to turn RAID off on my sata drives which was on by default on my Dell.

---


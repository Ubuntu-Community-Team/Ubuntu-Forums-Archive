---
title: "Instability in Karmic"
date: 2010-01-21
forum: General Help
---

### Post by joe_newbie on 2010-01-21
I skipped over Jaunty on my main desktop because Intrepid had been working perfectly for so long. Finally took the plunge to Karmic, and have had major instability problems. I cannot trace them to any particular program I am using. At first it seemed related to power management, since it would lock up every time it had a period of extended inactivity. I have disabled ACPI in my BIOS (I think), and any power management settings I could find in gnome to try to troubleshoot. That seems to have helped, but it still happens semi-regularly, sometimes when I am in the middle of using it. I have tried checking logs and googled anything that seemed important. ie a message in kern.log reads: Clocksource tsc unstable 

Anyone have suggestions for troubleshooting this?



Joe

---

### Post by fsando on 2010-01-26
The description of your problem is not very specific so it's hard to guess what may be wrong.

I recently went from intrepid to karmic too and have seen nothing but greateness (sorry for the "works-for-me").

My guess is that your problem is caused by a problematic driver for some piece of your hardware. The kernel in karmic has changed a lot - mostly huge improvements but there may be some specific hardware that has lost out for some reason.

dmesg will show you the boot process and maybe something failed there.

---

### Post by joe_newbie on 2010-01-26
My problem seems to have gotten better, still not what I would call stable but much better. For other people with instability in karmic I would refer you to this much more complete discussion of the various problems people seem to be having:

[http://ubuntuforums.org/showthread.php?t=1309015](http://ubuntuforums.org/showthread.php?t=1309015)

---


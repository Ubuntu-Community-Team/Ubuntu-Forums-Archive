---
title: "Live CD Boot issues"
date: 2010-01-17
forum: General Help
---

### Post by sandeepsblr on 2010-01-17
Hi,

I am trying to boot from the Ubuntu 9.10 live CD but it abruptly shut downs the system.

This is happening only from past few days after my XP sp2 got corrupted. My XP SP2 OS was also restarting during load (in splash screen). As both the OS was behaving the same I suspected Motherboard issue and got it checked. But no issues were found in it. Changed my RAM too (rather upgraded)

Hence I reinstalled XP on my HDD, it started to behave normally without any issues. Hence I suspected it was the corrupt MBR.

As I had already formatted by C drive the I thought the problem is solved. But when I tried to boot from the LIVE CD the issue remained... :(

Can anyone tell me what can be issue? Does anyone suspect any other hardware issue? Or if its the corrupt MBR how can i repair it?

Sorry about the long post but was necessary to explain the problem.

Any help on this greatly appreciated.

Thanks,
Sandeep

---

### Post by ajgreeny on 2010-01-17
Are you sure the live CD is a good one, burned from a good iso file, burned slowly, and not corrupted in any way?  I think there is an option at the boot screen of the live CD to check it out before you boot the OS.  Try that and at the end if it says there is a faulty file in the CD, you will need to check the mdd5sum of the iso file and also burn again if it really is good.

If the CD is good, then I think you may need to try F4, I think, to get the boot options and try using low graphics mode.

If that still does not work, you may need the Alternate Install CD, which as the name suggests is not a live CD, but gives you a text based installation. Still easy to use!

---


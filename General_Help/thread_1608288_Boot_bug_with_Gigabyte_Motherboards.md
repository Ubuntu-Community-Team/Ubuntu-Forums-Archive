---
title: "Boot bug with Gigabyte Motherboards?"
date: 2010-10-28
forum: General Help
---

### Post by poe503 on 2010-10-28
This thread [http://ubuntuforums.org/showthread.php?t=1539371&highlight=boot]("http://ubuntuforums.org/showthread.php?t=1539371&highlight=boot") was the only one I could find on this forum that addressed the problem I am having.  It also involved a Gigabyte motherboard.

I recently purchased a Gigabyte GA-MA770T-UD3 motherboard which is a version 1.3 .  I have a v. 1.0 of the same motherboard which I have used regularly for a year.

The problem I have is that newer versions of Ubuntu (10.04 and 10.10) don't boot reliably with the new motherboard.  It will boot up to where it says "Begin: Running /scripts/init-bottom. Done." and then will stop.  If I hit any key on the keyboard the boot finishes and everything is OK.

Sometimes it will hang like this but often it will boot successfully without assistance.  I need it to boot by itself reliably every time.

Older versions of Ubuntu (8.04 and 9.04) boot just fine with the new board.  If I put the drive with the 10.04 installation in my older Gigabyte v.1.0 computer, it boots reliably every time.

Interesting to note that Windows XP sp1 installs fine on the older v. 1.0 computer but I need XP sp2 in order to do a successful installation on the v 1.3.

I have stress-tested the new setup for 6 hours without incident and memtested the RAM for 4 hours without error.  I have even swapped RAM between the two with no resolution.

I can't find any thing in syslog to explain this.

It stops just before the splash screen comes up.  I removed splash with no positive result.

Help would be appreciated.  Thanks.

---

### Post by CharlesA on 2010-10-28
It probably has something to do with the sata drivers required.

Have you tried booting into recovery mode to see if there are any errors displayed?

---

### Post by poe503 on 2010-10-28
Thanks for the extremely quick reply.

No, I have not checked out recovery mode and will do as you suggest.

---

### Post by poe503 on 2010-12-18
**Way delayed update:**

Finding nothing to indicate a problem, I switched to 9.04 which worked well until I installed Mythtv.  On a cold start, the board would power on but not POST until I would do a hard reset.

I gave up and RMAed the damned thing.

I bought the only current AMD board of similar parameters: an AS Rock "770 Extreme 3"  

The board doesn't have the Gigabyte quality of construction but it doesn't give me any problems either. I don't use the USB3 or SATA3 ports that are available on it.

---

### Post by CharlesA on 2010-12-18
Definitely a mobo problem.

Glad you were able to find one that worked.

You can mark the thread as solved from thread tools. :)

---

### Post by poe503 on 2010-12-18
Done.  If "solved" means throwing the baby out with the bath water.:-s

---


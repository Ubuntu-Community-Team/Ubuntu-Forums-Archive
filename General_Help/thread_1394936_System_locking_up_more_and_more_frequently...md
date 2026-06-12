---
title: "System locking up more and more frequently.."
date: 2010-01-31
forum: General Help
---

### Post by minimustangs on 2010-01-31
Yes, it's true, Ubuntu is crashing with more frequency recently. I can't attribute it to anything specific either. Well except that when I have to hard-reboot it the routine disk check runs and will not complete. So I'm guessing that the drive is developing bad sectors or some such problem. Which is odd because in the scheme of things - my things - this drive isn't that old. So I have two questions...

1/ Is there a disk check / repair utility from WITHIN Ubuntu. Like I said the "routine" disk check that runs occasionally from boot stops, and it's not always at the same place.

2/ Is Ubuntu "hard" on laptops? I wonder if running Ubuntu could stress my laptop to premature failure due to a not-quite-so-well written power management, hard drive management or other module.

Just asking...

---

### Post by NightwishFan on 2010-01-31
If your disk supports it, you can view information in System -> Administration -> Disk Utility. Just highlight the disk and choose "More Information". I really do not know what the output means, but it does inform you if it may be failing.

As for a disk check, (I think) you can manually do that in recovery mode. You can access recovery mode from the boot menu. If you do not see a boot menu, hold in the left shift while booting.

---

### Post by minimustangs on 2010-01-31
> **NightwishFan said:**
> If your disk supports it, you can view information in System -> Administration -> Disk Utility. Just highlight the disk and choose "More Information". I really do not know what the output means, but it does inform you if it may be failing.

As for a disk check, (I think) you can manually do that in recovery mode. You can access recovery mode from the boot menu. If you do not see a boot menu, hold in the left shift while booting.

That's the kind of thing I'm looking for...except I don't have it in the menu??

---

### Post by NightwishFan on 2010-02-01
The option might have been removed.

Boot into a karmic live CD and run a disk check from there. I believe the disk utility is able to, if not, then install Gparted or use the command line.

---


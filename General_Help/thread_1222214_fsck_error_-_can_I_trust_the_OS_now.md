---
title: "fsck error - can I trust the OS now?"
date: 2009-07-24
forum: General Help
---

### Post by opus_az on 2009-07-24
Upon booting my 9.04 gave "An automatic file system check (fsck) of the root filesystem failed. Manual fsck must be performed, then the system restarted..." 

A quick google found someone saying to do a sudo fsck and to say yes to everything it wants to fix. So, I did that and I can now boot normally.

But can I trust this OS now? It's an employee computer at a remote location. I have it with me now so if I should just reinstall now's the time.

PS: apparently there's been a few times the computer has frozen (in their words gone to sleep but I have all power management off) and needing restarting. The last time they got this error.

TIA,
O.

---

### Post by SuperSonic4 on 2009-07-24
Would you check Windows after running a chkdsk? It's much the same concept

---

### Post by opus_az on 2009-07-24
OK, thanks. Since it seemed to fix all the files it needed I'll trust it. 

Would normally want to scan the disk for errors but haven't found how to do that yet. Tried booting a Live CD, unmounting the boot partition and doing a fsck -t ext3 -V -r /dev/hda. That came back clean but took just a moment, so no scanning there.

Thanks.

---


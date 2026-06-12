---
title: "RAID help"
date: 2010-08-02
forum: General Help
---

### Post by UltraAnders on 2010-08-02
I’ve got a SATA HDD which I use for storage connected to a (now quite old) RAID PCI card (HighPoint Rocket RAID 1520). I’ve added another (blank) HDD, same brand and size to the PCI card. Ubuntu (10.04) can see both hard drives and access data. I’d like to mirror (raid 1?) these HDDs.

Looking around this forum I’ve noticed quite a few people mentioning FakeRAID. Turns out that’s not quite the same as software RAID. Given how cheap the 1520 was, I suspect it’s FakeRAID rather than Hardware. Perhaps someone can confirm?

Given Ubuntu can see both HDDs, would this mean it’ll have the correct drivers to work with a hardware/fake raid?
A common recommendation is to use mdadm to create a software RAID. How does this work for partitions accessed from multiple Operating Systems including Windows XP?

Cheers! :biggrin:

---

### Post by cj.surrusco on 2010-08-02
Your card is in fact, fakeraid. I would recommend software RAID, as far as using it with Ubuntu. However, you will not be able to access Linux software RAID partitions whatsoever in Windows, as far as I know.

If you need to access the RAID drives in both OS's then you would need to set it up using fakeraid, which would be easy for Windows, just installing the driver, but may require more work to get it working in Ubuntu (You may be able to alter the driver for the other Linux distros).

---

### Post by prodigy_ on 2010-08-02
> However, you will not be able to access Linux software RAID partitions whatsoever in Windows, as far as I know.
Not exactly true. Linux hardware raid can be accessed from a Linux VM and shared with the main (host) OS.

---

### Post by UltraAnders on 2010-08-03
Great, thanks for the advice. :D I'm so glad I didn't just suck it an see by using the Highpoint BIOS menu and create an array!

Think I'll s/w RAID the Linux EXT3 partitions (I never access these from Windows), FakeRAID the Windows partitions (stop accessing these from Linux) and leave a partition of HDD un-RAIDed which I'll use to transfer large files between the OSs. Unless anyone can forsee an issue (and assuming this is possible!)? Would it be possible (and safe!) to access a Windows FakeRAID partition in read-only mode from Linux?

---


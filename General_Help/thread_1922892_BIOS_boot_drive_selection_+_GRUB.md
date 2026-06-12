---
title: "BIOS boot drive selection + GRUB"
date: 2012-02-09
forum: General Help
---

### Post by NoTheism on 2012-02-09
I have multiple HDDs and one contains Ubuntu, other OSs and GRUB v2(?).

Anyway, I usually select through the BIOS boot menu which HDD I want to boot to and I noticed a problem when booting to my drive with GRUB on it. The issue is that after I boot through GRUB to any OS on that drive, and I reboot to a different drive (in particular, one with Windows 7), the system reboots by itself after about 10 or 15 seconds.

To prevent this from happening, I have to _disable_ the drives (through the BIOS) I do not want impacted by booting through the GRUB drive before booting to it. I would like to find out why this happens and, possibly, how to fix it.

Thank you.

---

### Post by efflandt on 2012-02-09
Why not just boot everything from grub on whichever drive it is on.  I boot Win7 or Maverick on sda or 11.10 on sdb from 11.10's grub on sdb.

Although, in one case for a Win7 service pack update it wanted to be the master of its boot drive (standard dos/win mbr) in order for the update to succeed.  So Maverick's grub is on its own partition (sda4 instead of sda mbr).  Grub boots Win7 fine, but if I want to boot Win7 without going through grub, I just hit F12 during BIOS splash screen (Dell) and select my 1st drive.

---


---
title: "boot issues with grub2"
date: 2010-01-16
forum: General Help
---

### Post by TheWanderingMaverick on 2010-01-16
Yesterday I updated Ubuntu via update manager. I rebooted, selected ubuntu from MS bootloader, and came across grub2. The menu is not there, and I tried pressing shift without success. With each reboot, grub comes default instead of MS bootloader. I have tried using grub commands to boot into ubuntu, but I cannot find the appropreate sd (partition?). Is there a way to:
a. Get the grub menu back,
b. Get microsoft bootloader back,
c. Downgrade back to grub legacy (which I tried using Ubuntu live cd and that was useless)?
I need to do this without any loss of data whatsoever.

---

### Post by TheWanderingMaverick on 2010-01-16
Okay, I've suceeded in booting into XP using the following method at Grub command line, but I still can't get into ubuntu:

set root=(hd0,2)
chainloader +1
boot

---


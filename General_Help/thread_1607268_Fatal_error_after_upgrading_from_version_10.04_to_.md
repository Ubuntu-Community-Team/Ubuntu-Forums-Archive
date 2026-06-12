---
title: "Fatal error after upgrading from version 10.04 to 10.10"
date: 2010-10-27
forum: General Help
---

### Post by tnic on 2010-10-27
I upgraded Ubuntu from version 10.04 to 10.10. When the upgrade completed I was asked to reboot. After reboot I simply got the message "error: file not found" on the screen. After a few seconds the machine rebooted.

I guess it is the boot loader that was not found. Is there some hope of fixing this problem? 

Regards,

Tomas

---

### Post by AndyCee on 2010-10-28
If you have a liveCD (of Karmic or later) you can restore the GRUB2 bootloader using the instructions [here]("http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05").

Assuming the bootloader IS the problem, that is. If you press "shift" after the bios appears, do you get the GRUB menu?

---

### Post by tnic on 2010-10-28
Thanks for the reply. I found out that the easiest solution might be to reinstall Ubuntu.

---

### Post by AndyCee on 2010-10-28
If that's not too big a problem, then yes, that would be easier than troubleshooting GRUB :-) .

---


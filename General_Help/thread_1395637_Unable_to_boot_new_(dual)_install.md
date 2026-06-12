---
title: "Unable to boot new (dual) install"
date: 2010-02-01
forum: General Help
---

### Post by moodog on 2010-02-01
I previously had mythbuntu 8.04 installed, without a separate /boot partition. I then dist-upgraded all the way to 9.10. I want to do a separate install of 9.10 now though. I've carried out the install properly (installing to an ext4 partition), and when the machine next booted, there wasn't a new option in the grub menu. I booted into the old 9.10 mythbuntu, and edited the grub menu.lst adding a new entry for the new installation, with a root entry with the correct uuid etc. Then when I reboot and select this option, I simply get a "file not found" error.

So /boot is in the old partition for the original (ext3) mythbuntu 9.10 installation (/dev/sdd1), and the new installation is in an ext4 partition on /dev/sdd5 (inside an extended partition).

Is there anything special I need to be doing here, or should I be able to boot into either 9.10 installation?

---


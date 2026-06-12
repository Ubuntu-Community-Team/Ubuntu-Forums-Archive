---
title: "dmraid won't activate partitions - stuck at initramfs prompt"
date: 2012-04-15
forum: General Help
---

### Post by ByKeLaO on 2012-04-15
I have set up a dual-boot Windows 7/Ubuntu 12.04 Beta2 system on an Intel RAID 0 volume, using a GPT partition table, on a UEFI system. Legacy boot is disabled.

The installation of both operating systems completed successfully, and Windows 7 boots just fine. When I try to boot Ubuntu, I get dumped at the initramfs shell.

dmraid activated my RAID device but not the partitions on it. How can I activate the partitions in order to get the system to boot?

**Update**: Solution was to chroot into the installed system and run *apt-get install kpartx-boot*. Works great now!

---


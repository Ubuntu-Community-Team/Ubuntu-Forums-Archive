---
title: "grub refuses to install to RAID0 system after package upgrade"
date: 2012-09-18
forum: General Help
---

### Post by ronnodas on 2012-09-18
I  have a software raid 0 setup with dual booting Windows 7 and Ubuntu 12.04. The  GRUB bootloader that is already on the hard drive seems to work fine.  However, since the latest package update for grub, it refuses to install  the new version to the hard disk. grub-install throws the following  error:
 /usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/<raid name>_RAID0p9.  Check your device.map.
Auto-detection of a filesystem of /dev/mapper/<raid name>_RAID0p9 failed.
Try with --recheck.
If the problem persists please report this together with the output of "/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub" to <bug-grub@gnu.org>
 update-grub pops the same
"/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/<raid name>_RAID0p9.  Check your device.map."
every alternate line.
 I don't understand what exactly is going on. I'm afraid to reinstall  the grub package because it might mess up the boot, which currently  works fine. Is it safe to just ignore this?

---


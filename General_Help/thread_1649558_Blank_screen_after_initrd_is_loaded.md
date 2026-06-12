---
title: "Blank screen after initrd is loaded"
date: 2010-12-20
forum: General Help
---

### Post by BinaryMn on 2010-12-20
Yesterday night, I complied and installed the sk98lin driver for Marvell Yukon NICs. I habitually ran upgrade-initramfs -u.

Upon rebooting, I'm presented with a blank screen after GRUB starts trying to boot Ubuntu. It's not a busybox console and doesn't accept any commands. When I boot with the "quiet splash" arguments not included, the last thing I see scroll across the screen is something about the previous NIC driver (sky2) even though I made a modprobe rule to blacklist the driver.

The kernel I'm trying to use is 2.6.35-23. I still have a kernel and initrd compiled for 2.6.35-22 and can boot using that entry in GRUB. I'm currently at work and am unable to troubleshoot at the moment. I was going to attempt to rename both the sk98lin and sky2 modules for 2.6.35-23, update the initrd, and reboot and see if I get the same problem.

If anyone else a bit more experienced with what could cause something like this to happen and/or has any ideas or advice, it would be appreciated.

---


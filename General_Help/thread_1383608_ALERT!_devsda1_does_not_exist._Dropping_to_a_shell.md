---
title: "ALERT! /dev/sda1 does not exist. Dropping to a shell!"
date: 2010-01-17
forum: General Help
---

### Post by ajsquared on 2010-01-17
Since upgrading to Karmic I have been getting this message "Gave up waiting for root device...ALERT! /dev/sda1 does not exist. Dropping to a shell!" when booting.  I am then given an (initramfs) prompt.  If I type "reboot" here then my computer will generally boot without problems.  This does not happen on every boot; it almost always happens when my computer has been off more more than a few minutes.  It never happens when I do a restart.  I did a fresh install of Karmic a few days ago and I still am having the problem.  I have replaced the UUID for my hard drive in /etc/fstab and in the grub config.  I have also tried adding the boot options "pci=nomsi", "acpi=off", and "noapic".  None of these have resolved my issue.  I've attached a tarball with the following contents:
[LIST]
[*]/etc/default/grub
[*]/etc/fstab
[*]/boot/grub/grub.cfg
[*]busybox.txt
[*]blkid
[*]fdisk -l
[*]lspci -v
[/LIST]

busybox.txt is the output of commands when I am at the (initramfs) prompt.

---


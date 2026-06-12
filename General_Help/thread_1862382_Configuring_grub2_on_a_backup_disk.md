---
title: "Configuring grub2 on a backup disk"
date: 2011-10-16
forum: General Help
---

### Post by jdege on 2011-10-16
I'm running Ubuntu 10.04, and planning to upgrade.  Before I do, though, I want to make sure my backup/restore processes work.  My backups, of course, have been running since I first installed 10.04, but it's only a restore that can demonstrate that they have been running successfully.

And I've found a problem.  I don't know how to get grub2 configured correctly, on the restored disk.

Currently, my running system is on /dev/sda, with /boot on /dev/sda1 and / on /dev/mapper/desktop-root.  (I'm using logical volumes.)  This configuration has been running successfully for several years.

My restore is on /dev/sdb, with /boot on /dev/sdb1 and / on /dev/mapper/desktop2-root.

All of the files have been restored, and /etc/fstab has been edited, on the restored drive, to reflect the changed logical volume name.

But I only have grub installed on /dev/sda, so /dev/sdb is not bootable.

I'm not looking to do anything fancy.  I'm not trying to dual boot, I just want to be able to boot from /dev/sdb, using /dev/sdb1 as /boot, and /dev/mapper/desktop2-root as /.  In other words, I want to do to /dev/sdb exactly what running update-grub would do to /dev/sda, when I was booted off of /dev/sda.

Any ideas?

=== edit ===
Just to clarify, when I edited fstab, to set the changed logical volume name, I also updated the UUID of the /boot partition.

---


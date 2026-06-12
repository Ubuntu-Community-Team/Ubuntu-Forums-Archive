---
title: "How to backup/restore an encrypted root partition?"
date: 2011-11-06
forum: General Help
---

### Post by kurty_77 on 2011-11-06
Hi everyone,

I have an encrypted root partition (made by the alternate installer CD) that I would like to be able to backup/restore in case of failure.
I tried using fsarchiver to backup the root(/dev/sda1) and boot(/dev/sdc1) partitions.

I unlocked the root partition using the "disk utility" in the live-cd, then made a backup of each unmounted partition.
However when I restore the partitions (succesfully according to fsarchiver) it doesn't boot, I get a grub menu, but it always fails, with messages like "evms_Activate not available" etc.

Before one backup I changed the fstab and crypttab to be based on /dev locations, so I wouldn't have to worry about changing uuids, but this doesn't seem to fix the problem.

Anyone have any ideas what I am doing wrong?
I tried chroot-ing into the restored filesystem from the livecd and running grub-update, and/or grub-install, but that didn't help.

I have searched these forums and google to no avail.

---

### Post by kurty_77 on 2011-11-08
Anybody out there?

---


---
title: "Unable to boot due to changed UUID in RAID array"
date: 2010-05-09
forum: General Help
---

### Post by TheSilverHornet on 2010-05-09
Allo, I'm running 64bit Lucid.  I've recently had a severe problem with my softraid (5) array, and have had to recreate the array to fix it.  However this now means that something is up with GRUB/initramfs, and booting times out while waiting for the root  device (md0) to be ready.  /boot is on a normal partition, not the raid array itself.  A friend of mine has rebuilt my initramfs file with the new UUID, but now I get the message: 'Kernel panic - not syncing : VFS: unable to mount root fs on unknown-block (9,0)'.

So my question is either how do I sort this error, OR how do I rebuild initramfs/grub in a way that will boot?  I've been without a system for over a week now, pretty much at my wits end.

Many thanks in advance.

---

### Post by nikhilbhardwaj on 2010-05-09
boot from a live cd
find the new uuid with blkid
and make the changes to your fstab

when booting from grub choose the edit mode and change the uuid that should allow you to boot after which you can update grub

---

### Post by TheSilverHornet on 2010-05-09
I've already added the uuid to the boot line, root=UUID=$uuid, and I've edited fstab too... as fstab is on the array, it won't be being loaded at that point, so it must be something awry with /boot, initrd, or GRUB.  Thank you though. :)

---

### Post by TheSilverHornet on 2010-05-09
bumping

---

### Post by Ad@m on 2010-05-09
Perhaps you are experiencing a similar issue as discussed here but for a different reason.

[http://ubuntuforums.org/showthread.php?t=1477373](http://ubuntuforums.org/showthread.php?t=1477373)

Check your /boot/grub/grub.cfg has the initrd.img entry present for the kernel you are trying to boot into.

---

### Post by TheSilverHornet on 2010-05-09
It is present, cheers though.  :)

---

### Post by TheSilverHornet on 2010-05-11
Solution: boot from the alternate installer CD's 'Recover' option, set the root as the raid array, and update initramfs.

This doesn't solve the issue that caused the broken raid in the first place ... something in Ubuntu is literally wrecking my raid, specifics as yet unknown, but it's happened 3 times now, once within _10 minutes_ of repairing and rebooting the system. I've updated everything, but it's happened once since I did that... waiting on it to happen again so I can inspect it via SSH (when it happens I lose USB/PS2 input, and usually have to hard reset).

---


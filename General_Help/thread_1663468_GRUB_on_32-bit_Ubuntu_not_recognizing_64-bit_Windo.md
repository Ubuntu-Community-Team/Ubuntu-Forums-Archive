---
title: "GRUB on 32-bit Ubuntu not recognizing 64-bit Windows?"
date: 2011-01-09
forum: General Help
---

### Post by fraser_m on 2011-01-09
I installed Ubuntu this morning alongside Windows 7, but update-grub doesn't seem to be recognizing the Windows partition.

I've attached bootinfoscript's RESULTS.txt, any ideas?

EDIT: This is on Maverick.

---

### Post by oldfred on 2011-01-09
Windows 7 uses a 100MB hidden partition for boot/recovery. Your sda shows the boot flag but the windows boot files are missing.

You should be able to move the boot flag to sda2 and run the windows repairs to add the two missing boot files.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

Then run windows repairs to add the missing files.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---


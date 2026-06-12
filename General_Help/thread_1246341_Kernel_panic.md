---
title: "Kernel panic"
date: 2009-08-21
forum: General Help
---

### Post by tobeno on 2009-08-21
When I shut down and reboted my computer after having installed the latest updates, I got some very disturbing error messages:

0.3108661] ACPI: Aborted because of crc error
5.828225] crc error
5.856132] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

and the boot sequence halted.

I understand that I don't have access to the file system, but the rest of these error messages doesn't tell me much. Do I have to reformat the hard disk and reinstall the OS, or is there a simpler solution?

I sure hope someone can help me solving this problem. Luckily I have recent backups of the entire home-folder, so I haven't lost much data files.

Tom E.

---

### Post by P4man on 2009-08-21
try booting the previous kernel in grub menu.

Is it possible you updated everything, but not the kernel ?
Im basing my guess on this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302308](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302308)

(see last messages).

---

### Post by tobeno on 2009-08-21
Thank you very much for your advice - the computer booted normally with the previous kernel. There are no more new updates available, so I guess I have not missed anything there. But I could not find why the new kernel didn't manage to mount the file system. In my opinion this update should never have been released.

---


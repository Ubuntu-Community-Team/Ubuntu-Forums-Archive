---
title: "is my hard drive going bad?"
date: 2010-08-29
forum: General Help
---

### Post by anextx on 2010-08-29
When I try to start up 9.10 I can get past GRUB but not fsck.  A file check will be started but no progress will be made and finally I get the 'General error mounting filesystems'.

Trying in recovery mode I get this just before the fsck check

> fsck from util-linux-ng 2.16
[8.016378] ACPI: I/O resource piix4_smbs [0xb00-0xb07] conflicts with ACPI region SOR 1 [0x0b00-0xb0f]

/dev/sda1 goes fine

> /dev/sda3 has been mounted 34 times without being checked, check forced
mountall: canceled
/dev/sda: e2fsck canceled
fsck.ext4: Inode bitmap not loaded while setting block group checksum info
mountall: fsck /home [863] terminated with status 8
mountall: general fsck error
init: mountall main process terminated with status 1

This seems to be slightly different than the other threads I've seen discussing this issue.  It just all of a sudden happened, I didn't upgrade anything or have any crashes immediately prior.  

can anyone point me in the right direction?

---

### Post by arrange on 2010-08-29
You have to *fsck* the drive manually, preferably from a LiveCD, either via GParted (Partition &#8594; Check), or [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```
sudo fsck -fv /dev/sda3
```

---

### Post by anextx on 2010-08-29
Thank you sir, I wish all of my problems were so easy.

---


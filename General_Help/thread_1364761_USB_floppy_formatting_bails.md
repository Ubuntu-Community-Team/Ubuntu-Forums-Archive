---
title: "USB floppy formatting bails?"
date: 2009-12-26
forum: General Help
---

### Post by rvndrk3233 on 2009-12-26
Ive tried as root and installing ufiformat.

mkfs and mkdosfs seem to do same thing.
My fstab is set correctly, but I cant for like of me format the disk as vfat/msdos.

If I could format the disk ok, it would come up on the desktop.

Im working on a bootsector example and need access to a floppy.Note that 9.04 wont automount on the desktop, either.This worked on 9.10.

anyone have any FREEDOS tools? I cant seem to boot the cd with the usb floppy connected to copy over what I need.FREEDOS crashes randomly.

I get this after formatting:

$ dmesg|tail

[  524.641569] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  524.897426] sd 7:0:0:0: [sdd] 2880 512-byte hardware sectors: (1.47 MB/1.40 MiB)
[  525.025350] sd 7:0:0:0: [sdd] Write Protect is off
[  525.025356] sd 7:0:0:0: [sdd] Mode Sense: 00 4c 94 00
[  525.025359] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[  525.025366]  sdd: unknown partition table

(could specify mkfs with -I, but this doesnt change)

[  617.135348] FAT: invalid media value (0x5a)
[  617.135354] VFS: Can't find a valid FAT filesystem on dev sdd.
[  617.519139] FAT: invalid media value (0x5a)
[  617.519145] VFS: Can't find a valid FAT filesystem on dev sdd.

0x5a, isnt that a bootsector byte?

---


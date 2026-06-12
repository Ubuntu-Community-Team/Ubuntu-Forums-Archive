---
title: "turn off card reader auto-mount"
date: 2009-09-11
forum: General Help
---

### Post by ruuden on 2009-09-11
I'm trying to format a 4GB cf card but I get the error you see below. I think it is because the card reader automaticaly mounts the cf card, but I'm not sure. Does anybody know how to turn off auto-mount or how to deal with this error?

```

Command (m for help): Building a new DOS disklabel with disk identifier 0x5
62bc38a.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(ri
te)

Command (m for help): Command action
   e   extended
   p   primary partition (1-4)
Partition number (1-4): First cylinder (1-971, default 1): Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-971, default 971): Using default value 971

Command (m for help): Partition number (1-4):
Command (m for help): The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdc1 is mounted; will not make a filesystem here!
tune2fs 1.40.8 (13-Mar-2008)
tune2fs: Bad magic number in super-block while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

```

---

### Post by P4man on 2009-09-11
if its mounted, unmount it manually.
```
sudo umount /dev/sdc1 
```
to unmount it.

---


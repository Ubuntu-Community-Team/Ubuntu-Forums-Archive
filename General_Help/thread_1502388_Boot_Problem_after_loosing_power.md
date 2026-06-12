---
title: "Boot Problem after loosing power"
date: 2010-06-05
forum: General Help
---

### Post by Nano3.14 on 2010-06-05
Firstly, sorry if this is the wrong place for this, im not sure where boot errors would go.

after someone accidentally kicked the power cord for a server out of the wall,the server fails to boot. upon reconnecting.
this is the output i get:

```
fsck from util-linux-ng 2.6
/dev/sda5 was not cleanly unmounted, check forced.
filesystem checks are in progress (ESC to cancel)
/dev/sda5: 165/124496 files (4.8% non-contiguous), 32210.248976 blocks
mountall: fsck /boot [382] terminated with status 1
fsck from util-linux-ng 2.16
/dev/mapper/Locke-root: clean, 50023/1185520 files, 291893/473496 blocks
```

at which point whatever process is running this just doesn't end (or at least it doesn't accept input of any kind)

is there an easy fix for this?

thanks

---

### Post by gzarkadas on 2010-06-14
It looks like your separate /boot partition has problem; thus the kernel cannot load properly.

You will have to boot with a liveCD and mount and correct the /boot partition. 

If your current kernel files cannot be repaired you will then either have to:

[LIST]
[*]restore /boot from a backup or
[/LIST]

[LIST]
[*]select another kernel as default.
[/LIST]
[INDENT]
[LIST]
[*]For Grub2: edit /etc/default/grub (I am now at a grub-legacy system, so see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for details) and then run update-grub.
[*]For Grub-legacy: edit /boot/grub/menu.lst. Search for the line "default <number>" at the top of the file and set it to an appropriate value (2 or 4 usually).
[/LIST]
[/INDENT]If the /boot partition is physically damaged, you can copy your backup files to the /boot directory in your root (/) partition and comment out the /boot partition line in /etc/fstab. Since you are changing the partition of your kernel(s) you will need to update your grub or grub-legacy config also (see above).

---


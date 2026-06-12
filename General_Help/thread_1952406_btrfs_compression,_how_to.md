---
title: "btrfs compression, how to?"
date: 2012-04-04
forum: General Help
---

### Post by brexsis on 2012-04-04
here is my fstab file:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d7c68c5b-43ee-47e4-a855-75aa01d660be /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=2348bfc7-f013-4c62-bccf-46f8314a26ed /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=d7c68c5b-43ee-47e4-a855-75aa01d660be /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda5 during installation
#UUID=8f97f921-ec82-44af-86dd-b033c5b6009b none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

How can i add btrfs compression option?
i tried to add "compress=lzo", and just "compress" in / and /home mount options, restarted pc, but nothing changed, folder size didnt change, fs-mark score was the same...

So how do i get compression to work? kernel version - 3.0.0-12-generic

---

### Post by LewisTM on 2012-04-04
Compression only affects newly written files, not old ones.
To compress everything you would have to backup and restore to your btrfs partition.
There is also talk that defragmenting the fs would recompress everything but I'm not sure that works since btrfs defrag is unconventional.

Cheers!

---

### Post by brexsis on 2012-04-04
then if i copy that 1 folder that i am monitoring to other place, then it should be compressed?

and why fs-mark results dont change?

---

### Post by LewisTM on 2012-04-04
Yes.
Be aware though that Linux tools may not accurately report the allocated/free space of a btrfs filesystem because it's still new and there's no way to know how much physical space each file takes when compressed. 
See [https://btrfs.wiki.kernel.org/articles/f/a/q/FAQ_1fe9.html#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F](https://btrfs.wiki.kernel.org/articles/f/a/q/FAQ_1fe9.html#Why_are_there_so_many_ways_to_check_the_amount_of_free_space.3F)

---


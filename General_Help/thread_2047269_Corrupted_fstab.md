---
title: "Corrupted fstab"
date: 2012-08-24
forum: General Help
---

### Post by Aegresco on 2012-08-24
I accidentally copied over five million lines of gibberish to my fstab file. After, also accidentally, rebooting, the hard drive won't mount and I'm stuck in a terminal. When running fsck it aborts, saying that the buffer limit is reached at just above 5100000. Can someone help me reset fstab?
I'm using 12.04 64 bit.

---

### Post by cortman on 2012-08-24
Try booting from a live CD, mount the root partition, and run

```
less etc/fstab
```

When you're in the mounted partition, it can give you an idea if it is salvageable (i.e., if it just has a bunch of gibberish appended to it).

---

### Post by Ms. Daisy on 2012-08-24
Wow. Can you use a live CD to run fsck?

---

### Post by ajgreeny on 2012-08-24
The default fstab ion 12.04 looks like
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=01b9131d-43fe-4b4e-be2b-b319de5a898a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bfd912d-b6b6-4a68-9aaf-4139513772ec none            swap    sw              0       0
[COLOR=Red]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/COLOR]
```but with your own/dev/sdx# names and UUIDs for the various partitions, and probably no final line for a floppy disk (shown in [COLOR=Red]red[/COLOR]).

If you have a separate /home partition you may need extra lines in the format
```
# /home was on /dev/sda2 during installation
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
```again with your own UUID for/home.

You can find your own UUIDs from a live system by running ```
sudo blkid -c /dev/null
```and it may be worth trying your own UUID version of this fstab, if you can't edit out the gibberish that you added with a live CD, as suggested by cortman.

I don't think running fsck from a live system will help as there is no filesystem corruption to worry about, just an incorrect fstab which is not allowing the system to boot.

---

### Post by Aegresco on 2012-08-24
Thanks all! I've got it back up and everything seems to be working fine.

---


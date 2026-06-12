---
title: "Error loading os after raid setup"
date: 2009-12-03
forum: General Help
---

### Post by piusvelte on 2009-12-03
I am migrating to a software raid1 and performed the following steps, but can't boot it:

Originally, I was running off of a single IDE drive (/dev/sda), with the default ubuntu partition scheme.

I added 2 identical SATA drives (/dev/sdb, /dev/sdc), partitioned one using the default ubuntu partition scheme and then used sfdisk to copy the table to the second. Both are marked bootable and with the types set as Linux Raid (fd).

I created 2 raid1 arrays:
 /dev/md0 from /dev/sdb1 /dev/sdc1 for "/"
 /dev/md1 from /dev/sdb5 /dev/sdc5 for swap

I updated mdadm.conf, and made the filesystems on both arrays.

I updated /etc/fstab and /etc/mtab to use /dev/md0 and /dev/md1

I updated /boot/grub/menu.lst, adding "fallback 1", duplicating the first boot block and updating the UUIDs to match those of sdb1 and sdc1

```

# update-initramfs -u

```
```

# grub
grub> root (hd0,0)
grub> setup (hd0)

```
```

# cd /
# mount /dev/md0 /mnt
# cp -dpRx . /mnt/md0
# umount /mnt

```
```

# shutdown -hP now

```

I pulled the originally IDE drive out, booted, updated the drive order in the bios, and I receive the message:
```

Error loading the OS

```

If I put the IDE drive back in, it boots with the arrays as root and swap, just as intended.

I think that this may have to do with the device mapping changing, but I'm not sure. What should I check or try to get this to boot off of the array without the obsolete drive running? Thanks!

---


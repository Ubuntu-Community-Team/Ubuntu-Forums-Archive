---
title: "Problems Configuring GRUB"
date: 2009-08-29
forum: General Help
---

### Post by AVW on 2009-08-29
Just a quick question on configuring GRUB, I'm trying to make GRUB able to be able to boot Ubuntu, a Windows partition (sadly WINE can't do everything), and another flavor of Linux (the necessary info is included). I can only boot into Ubuntu, I've tried a bunch of things to get the other distro to work, to no avail. Any help would be lovely!

```
MENU.LST EXCERPT

title Ubuntu 9.04, kernel 2.6.28-15-generic
    uuid        94b62394-a300-47cd-9caf-d430e61e5682
    kernel      /boot/vmlinuz-2.6.28-15-generic root=UUID=94b62394-a300-47cd-9caf-d430e61e5682 ro quiet splash 
    initrd      /boot/initrd.img-2.6.28-15-generic
    quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
    uuid        94b62394-a300-47cd-9caf-d430e61e5682
    kernel      /boot/vmlinuz-2.6.28-15-generic root=UUID=94b62394-a300-47cd-9caf-d430e61e5682 ro  single
    initrd      /boot/initrd.img-2.6.28-15-generic
    quiet
title Ubuntu 9.04, memtest86+
    uuid        94b62394-a300-47cd-9caf-d430e61e5682
    kernel      /boot/memtest86+.bin
    quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
// removed because of obviously wrong and possibly confusing info
title Sabayon // I tried putting link to the Sabayon boot folder, putting the ink in Ubuntu's boot folder and using that directory, (/boot/sabayon instead of /boot in the kernel/initr dir) but it didn't work. I also tried putting the image in the Ubuntu boot folder, but that didn't work either.
    uuid        4507c5ca-1032-41cb-aedf-20613f5bd293
    kernel        /boot/kernel-genkernel-x86-2.6.29-sabayon root=UUID=4507c5ca-1032-41cb-aedf-20613f5bd293 ro
    initrd        /boot/initramfs-genkernel-x86-2.6.29-sabayon
``````
SOME INFO ABOUT PARTITIONS

// The 'tree'

=======================
/dev/sda-------
------/dev/sda1 // Ubuntu partition
------/dev/sda2 // Ubuntu swap
=======================
/dev/sdb-------
------/dev/sdb1 // Windows XP partition
------/dev/sdb2 // Sabayon
=======================

// The Ubuntu device.map file

(hd0)    /dev/sda
(hd1)    /dev/sdb

// The mount command output (sans unnecessary stuff)

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) // Windows XP partition
/dev/sdb2 on /media/% type ext4 (rw,nosuid,nodev,uhelper=hal) // Sabayon partition

```

---

### Post by AVW on 2009-08-30
Will anyone help me?

---

### Post by Vishnu V on 2009-08-30
Add the following lines after  title Windows on menu.lst file
```

root	(hd1,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by dandnsmith on 2009-08-30
That probably won't work (several reasons), more info is needed about how the Windows stuff was installed (eg was the Windows disk the first when it was installed)

---


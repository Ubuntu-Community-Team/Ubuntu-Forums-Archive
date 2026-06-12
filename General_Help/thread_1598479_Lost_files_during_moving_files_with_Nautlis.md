---
title: "Lost files during moving files with Nautlis"
date: 2010-10-16
forum: General Help
---

### Post by pwn on 2010-10-16
I was moving a folder using Nautilus from an internal drive to a USB drive when suddenly, the power failed and the system rebooted before the UPS could go into backup. After I booted the PC again, half the files are are in neither of the drives. Do they go into a temporary folder first? There's nothing in /tmp and there's no Lost+Found folder.

Is there anyway to get back those files?

I'll always copy and delete from now on instead of moving.:(

---

### Post by dcstar on 2010-10-16
> **pwn said:**
> I was moving a folder using Nautilus from an internal drive to a USB drive when suddenly, the power failed and the system rebooted before the UPS could go into backup. After I booted the PC again, half the files are are in neither of the drives. Do they go into a temporary folder first? There's nothing in /tmp and there's no Lost+Found folder.

Is there anyway to get back those files?

I'll always copy and delete from now on instead of moving.:(

If you did not have a decent journaling file-system on the USB device then you have probably lost the files. Crap filesystems like FAT32 are the worst things that can be used when something like this occurs.

You can try and do a fsck on the USB device and you might get some files back.

---

### Post by pwn on 2010-10-17
```

[pwn@desktop ~]$ sudo e2fsck /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
Archive has been mounted 151 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

Archive: ***** FILE SYSTEM WAS MODIFIED *****
Archive: 17241/61054976 files (9.7% non-contiguous), 33339282/244190000 blocks

```

Still can't find those files.

---


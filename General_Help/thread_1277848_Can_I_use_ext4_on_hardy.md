---
title: "Can I use ext4 on hardy?"
date: 2009-09-28
forum: General Help
---

### Post by krelverehan on 2009-09-28
Hi... I am currently using LinuxMint 5 (based on the might Hardy Heron) and I have aquired a hdd formatted in ext4 with some data I would like to upload to my computer. I can't seem to access the drive what so ever.

my [FONT="Courier New"]** sudo fdisk -l**[/FONT] for the drive looks like:

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019e6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
```

Trying to open the hdd I get:

```
Cannot mount volume
The volume 'Videos' uses the ext4 file system which is not supported by your system.
```

Gparted is being of no help either.

Thanks!
-Krel

---

### Post by snowpine on 2009-09-28
ext4 requires kernel 2.6.28 or newer. I installed a newer kernel on my Hardy box partly so that I could read ext4 disks.

If it's just a one-time thing, I recommend simply booting with a Jaunty live CD, then copying the files over onto your Hardy drive. Easiest solution without making permanent changes.

---

### Post by falconindy on 2009-09-28
> **snowpine said:**
> ext4 requires kernel 2.6.28 or newer. I installed a newer kernel on my Hardy box partly so that I could read ext4 disks.

If it's just a one-time thing, I recommend simply booting with a Jaunty live CD, then copying the files over onto your Hardy drive. Easiest solution without making permanent changes.
No. ext4 was introduced in 2.6.19, but it wasn't until 2.6.28 that ext4 was considered stable. It may be that ext4 support was not compiled into the generic Hardy kernel.

---

### Post by krelverehan on 2009-09-29
> **snowpine said:**
> ext4 requires kernel 2.6.28 or newer. I installed a newer kernel on my Hardy box partly so that I could read ext4 disks.

If it's just a one-time thing, I recommend simply booting with a Jaunty live CD, then copying the files over onto your Hardy drive. Easiest solution without making permanent changes.

Thanks snowpine! I used my friend's bootable usb key with Jaunty and did the switcharoo.

---


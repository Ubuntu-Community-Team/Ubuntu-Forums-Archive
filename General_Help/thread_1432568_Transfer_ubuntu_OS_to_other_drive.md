---
title: "Transfer ubuntu OS to other drive?"
date: 2010-03-17
forum: General Help
---

### Post by ubuntüser on 2010-03-17
I have this as my current setup:
/dev/sda 1TB drive in RAID 1 \ RAID 1 together
/dev/sdb 1TB drive in RAID 1 / with this drive
/dev/sdc 160GB drive as OS drive

I have the grub bootloader on sdc, the pc booting order is SDC first.

the raid 1 array is mounted as /media/raid

Is there any way to transfer my whole / system to the RAID 1 drives and put the bootloader on there, and get rid of the 160GB drive altogether without disrupting anything.

I know I would have to change quite a bit of stuff (all the stuff referring to /media/raid basically), but I don't want an OS drive that may fail at some point.

---

### Post by prodigy_ on 2010-03-17
Boot from Live CD. Use ```
fdisk -l
``` to check partition names. Then use ```
dd if=/dev/<source_partition> of=/dev/<target_partition>
```

---

### Post by dcstar on 2010-03-18
> **ubuntüser said:**
> I have this as my current setup:
/dev/sda 1TB drive in RAID 1 \ RAID 1 together
/dev/sdb 1TB drive in RAID 1 / with this drive
/dev/sdc 160GB drive as OS drive

I have the grub bootloader on sdc, the pc booting order is SDC first.

the raid 1 array is mounted as /media/raid

Is there any way to transfer my whole / system to the RAID 1 drives and put the bootloader on there, and get rid of the 160GB drive altogether without disrupting anything.
.........

Since the current system boots without RAID, I doubt it will work correctly if transferred to a RAID environment.

You may be better off doing a proper install onto the RAID array.

---

### Post by ubuntüser on 2010-03-18
> **prodigy_ said:**
> Boot from Live CD. Use ```
fdisk -l
``` to check partition names. Then use ```
dd if=/dev/<source_partition> of=/dev/<target_partition>
```

Yea, but that wouldn't work, because I also have 600GB of data on my RAID Drives. I want to move my root partition.

the RAID drives are EXT3 and the other one is EXT4.

How hard is it installing the ubuntu OS onto the raid drive without disturbing the other contents of the raid drive?

---

### Post by ubuntüser on 2010-03-18
I know this sounds weird but I want to know if its possible:

Make a 10GB .iso file (or similar) on my RAID1 array, and mount that on / and boot from it, mount the raid array on /media/raid

My actual ubuntu installation is ~4GB, and I don't think its ever going to to above 10GB. So is this possible and a good idea?

---


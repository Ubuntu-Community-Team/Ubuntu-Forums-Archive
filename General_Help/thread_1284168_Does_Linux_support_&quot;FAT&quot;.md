---
title: "Does Linux support &quot;FAT&quot;?"
date: 2009-10-06
forum: General Help
---

### Post by Roasted on 2009-10-06
I know Linux supports FAT32, but I'm dealing with a curve ball here.

Two flash drives.

8gb - FAT32 - Works.
512mb - FAT - Doesn't Work.

However, the 512mb flash drive does not work in Linux. It's just not recognized. GParted sees no existence of it, however the 8gb FAT32 drive works perfectly fine.

In Windows, the 512mb flash drive is noted as "FAT".

Does Linux support "FAT"?

---

### Post by cdenley on 2009-10-06
> **Roasted said:**
> Does Linux support "FAT"?

Yes. Post this output while the device is connected.
```

sudo fdisk -l

```

---

### Post by StuartN on 2009-10-06
> **Roasted said:**
> Does Linux support "FAT"?

Yes, try **lsusb** to check that it is recognised and **sudo fdisk -l** to get some stats, e.g.:

```
Disk /dev/sdb: 124 MB, 124780544 bytes
16 heads, 32 sectors/track, 476 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xcc186729

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         476      121840    6  FAT16
```

---

### Post by Roasted on 2009-10-06
I think there's something wrong with the flash drive.

I plugged it in to an XP machine once, and it said USB device not recognized. Confused, I unplugged it and plugged it back in later. It worked. I saw there was only 1 file on it so I copied it to my desktop. Later, I tried the same scenario again. In fact, I tried it about 75 times. Each and every single time Windows XP said "USB device not recognized." 

I couldn't get it to respond again no matter what I tried. I think this flash drive is shot. It's a no-namer 512mb flash drive from who knows how long ago.

I should have tried sudo fdisk -l but when it came to my attention to try it, I was trying it with a Xandros laptop and I have no idea how to get to terminal in that thing.

---


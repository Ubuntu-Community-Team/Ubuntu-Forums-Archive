---
title: "Total filesystem capacity"
date: 2012-08-23
forum: General Help
---

### Post by JamesAng on 2012-08-23
Hi,

I've 3x 2TB hard drives and already partitioned for usage.
/dev/sda2 is the root filesystem and the remaining /dev/sdb1 and /dev/sdc1 are mounted to /mnt/hdd2 and /mnt/hdd3.

Using Disk Usage Analyzer, it reported Total filesystem capacity of 5.5TB (which is correct) by the detailed breakdown below only shows 2.3TB total for /.

Shouldn't I see 5.5TB for / instead?

Thank you.

---

### Post by SlugSlug on 2012-08-23
nope,

/ = /dev/sda2

try ```
df -h 
```

in terminal to give you an idea

---

### Post by oldfred on 2012-08-23
A full install takes about 4.5GB. After many updates and the addition of a lot of software I have about 7GB used. I normally use about 25GB for / and have all my data in other partitions.

If you have / as the entire 2TB drive, you may have files all over the drive. I think Ubuntu tries to optimize system somewhat but file system normally scatters files about. Not like NTFS that tries to pack everything at the beginning of the drive and a rewrite to a larger file requires a new copy at the end of the used space.

So for efficiency a  smaller / may be better.

---


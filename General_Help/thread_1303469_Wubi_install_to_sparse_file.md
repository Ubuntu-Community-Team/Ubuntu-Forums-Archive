---
title: "Wubi install to sparse file?"
date: 2009-10-28
forum: General Help
---

### Post by yottabit on 2009-10-28
I have a (small) SSD in the lappy, and every byte counts. Luckily sparse files can accomplish a lot for me with my TrueCrypt image, allowing it to grow as-needed without taking up the "max" space at first.

I'd like to find out if there is a way to get Wubi to install into a sparse file too, or even convert the file to sparse later. Ideally I could create a sparse wubi root.disk of 10 or 20 GB, so that it would only occupy the 2-3 GB of initial required storage, and grow dynamically as I use it.

On a HDD-based system this would likely suck because the fragmented growth of the sparse file would make the system crawl, but for an SSD it's a non-issue. On SSDs fragmentation is a good thing.

I have attempted to use the XP fsutil.exe utility to set the root.disk sparse setting to true, but it didn't have an effect. After doing so I even copied the file hoping XP would make it sparse by copying since the sparse setting was true, but it still didn't have an effect.

Does anyone know how to either:

1. Tell Wubi to create the sparse file from the install*, or

2. Convert the root.disk into a sparse file in XP?


* Regarding #1 above, if I can somehow find out how Wubi creates the virtual disk, and if it's using dd, I could tweak it very easily. For instance, if it's doing something like "dd if=/dev/zero of=root.disk bs=1M count=4000" for a 4 GB file, a simple change to "dd if=/dev/zero of=root.disk bs=1 seek=4G count=0" would change it to a 4 GB sparse file.

Thanks!!

J

---


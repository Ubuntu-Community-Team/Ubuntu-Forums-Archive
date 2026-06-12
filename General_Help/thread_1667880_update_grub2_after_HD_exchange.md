---
title: "update grub2 after HD exchange"
date: 2011-01-15
forum: General Help
---

### Post by RikoW on 2011-01-15
Dear all,

I exchanged the hard disk on my laptop after copying all partition over using a live DVD of Ubuntu.

I tried to re-install grub2 in the MBK by mounting the hd in the live session on doing:

```
sudo grub-install --root-directory=/media/sda1 /dev/sda
```

That indeed created a grub menu for boot, however the machine would not boot because apparently the UUIDs for the partitions have changed because of the new disk and the partition cannot be founf by its (old) UUID.

If I manually edited grub.cfg and use /dev/sda1 instead of the UUID it works. However, I'm sure that's not the proper way to do it.

How do I reinstall grub2/MBK properly after a hd change. Of course I could just re-install the system, but that I wanted to avoid.

Thanks and cheers,
        Riko

---


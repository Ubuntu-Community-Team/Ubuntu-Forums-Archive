---
title: "Resize partition, UUID changes?"
date: 2009-07-24
forum: General Help
---

### Post by tokico on 2009-07-24
Hi!

I have my disk like this:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x468b8849

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31236   250903138+   7  HPFS/NTFS
/dev/sda2   *       31237       32386     9237375    7  HPFS/NTFS
/dev/sda3           32387       38913    52428127+  83  Linux
```

Being sda1 my Windows Vista Partititon, sda2 the recovery partition that came with my laptop and sda3 my Ubuntu Jaunty Installation.

I want to resize my windows partition to 80gb and to create sda4 with the resulting free space. My question is:

If I do that will the UUID of my Ubuntu partition change?
Will I run into any boot/GRUB problems?

thanks, tokico.

---

### Post by Cheesemill on 2009-07-24
The UUID won't change, that's the whole point of using them instead of drive letters / partition numbers.
 
Also is there a reason you don't have any swap space?

---

### Post by drs305 on 2009-07-24
No, your Ubuntu partition UUID should not change. However, after you have done the repartitioning it would be good to check the UUIDs with the following command:
```

sudo blkid -c /dev/null

```

This will provide the UUIDs of your partitions. At that time, you may wish to change the device designations in fstab from "sdXX" to UUIDs.

Also compare the UUIDs above with those in your menu.lst just to be sure they are the same:
```

cat /boot/grub/menu.lst

```

---

### Post by tokico on 2009-07-24
> **Cheesemill said:**
> The UUID won't change, that's the whole point of using them instead of drive letters / partition numbers.
 
Also is there a reason you don't have any swap space?

I have 4GB of RAM, I don't think I need Swap, IMHO.

I understand the need of Swap, I have an older system with 512 MB and without Swap it's a pain in the *ss.

---


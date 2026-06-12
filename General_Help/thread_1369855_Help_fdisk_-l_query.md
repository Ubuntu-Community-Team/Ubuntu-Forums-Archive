---
title: "Help fdisk -l query"
date: 2010-01-01
forum: General Help
---

### Post by whitetimer on 2010-01-01
Hi All

Ok i am new to Ubuntu, well been my main OS for a week now and i love it, though had a few crashes & clean installs, but prefer to do this than go back to Windows .... :P

Anyway, i have a 250gb sata drive that i think got a little messed up and now i am missing about 20gb ... its kind of weird ...

I have just done fdisk -l and this is my result 

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a52e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29271   235119276   83  Linux
/dev/sda2           29272       30401     9076725    5  Extended
/dev/sda5           29272       30401     9076693+  82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7955 MB, 7955021824 bytes
228 heads, 43 sectors/track, 198 cylinders
Units = cylinders of 9804 * 4096 = 40157184 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         199     7768572    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(120, 227, 43) logical=(198, 22, 6)

Disk /dev/sdc: 4005 MB, 4005560320 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x000f0656

   Device Boot      Start         End      Blocks   Id  System


```

I am not sure what /dev/sdb1 is and not sure it sure even be there.  Could that have anything to do with my missing HDD space ....

Many thanks for help

Whitetimer

---

### Post by whitetimer on 2010-01-01
Never mind, that was my mp3 player i had plugged in at the time ... duh

---

### Post by warfacegod on 2010-01-12
20 GB is about what you would expect because of system reserve. The default is 5%. You can use this to change it:

```
tune2fs -m x /dev/sda1
```

x is the % so if you want 1% change x to 1

---

### Post by warfacegod on 2010-01-12
sda1 is your boot drive. It's where Linux resides. You probably don't want to use 0%

---


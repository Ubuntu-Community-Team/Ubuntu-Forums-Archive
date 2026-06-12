---
title: "Deleting ubuntu"
date: 2010-02-23
forum: General Help
---

### Post by sincerelyydavid on 2010-02-23
so i'm having way too many problems with ubuntu. it's frustrating me. how can i delete its partition? i still have windows on a dual boot.

---

### Post by switch10 on 2010-02-23
You want to dual boot windows and what?  Use a Live CD and gparted to delete the ubuntu partition.

---

### Post by lorsen on 2010-02-23
If you want to try a different operating system you can just format/override the partition.
If you want to have windows alone you can delete the ubuntu partition and resize the windows partition.

---

### Post by coffeecat on 2010-02-23
If you have a conventional dual-boot (i.e., not Wubi) and you delete the Ubuntu partition, you won't be able to boot into Windows. Not until you repair the Windows MBR, that is. That's because some of grub is in the Ubuntu root partition.

If you need to repair the Windows MBR you can:

1 - Run FIXMBR from a Windows install disk. It must be a Microsoft disc, not an OEM image disc.

2 - If you don't have a Windows install disc, the easiest way (that I know of) of repairing the Windows MBR is with [SuperGrubDisk]("http://www.supergrubdisk.org/").

---


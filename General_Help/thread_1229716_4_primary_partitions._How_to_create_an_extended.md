---
title: "4 primary partitions. How to create an extended?"
date: 2009-08-02
forum: General Help
---

### Post by tokico on 2009-08-02
I have 4 primary partitions, but I want to create an extended to add more partitions as needed.

See fdisk -l:

```
antonio@portatil:~$ sudo fdisk -l
[sudo] password for antonio: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x468b8849

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11655    93618756    7  HPFS/NTFS
/dev/sda2           11656       12805     9237375    7  HPFS/NTFS
/dev/sda3           12806       19332    52428127+  83  Linux
/dev/sda4           19333       38913   157284382+   7  HPFS/NTFS
```

sda1 - my Windows Vista partition
sda2 - recovery partition that came with the laptop
sda3 - Ubuntu 9.04
sda4 - ntfs partition that I use to share files between Windows&Ubuntu.

Here's my problem: I want to create an extended partition and put sda4 in it, so it will be sda5. But how can I do that without copying the contents of sda4 to sda1 or sda3, deleting sda4, creating extended in sda4, creating sda5 and putting in it the backup files.

Thanks.

---

### Post by credobyte on 2009-08-02
Do you want to "convert" your primary sda4 to extended sda5 while not loosing any of your data ( sorry, didn't really understand what you want ) ?

---

### Post by tokico on 2009-08-02
> **credobyte said:**
> Do you want to "convert" your primary sda4 to extended sda5 while not loosing any of your data ( sorry, didn't really understand what you want ) ?

Yes, exactly.

---

### Post by credobyte on 2009-08-02
> **tokico said:**
> Yes, exactly.

Impossible! You'll need a temporary storage for your sda4 files ( so you could delete it, create a new extended partition and move them back ).

---


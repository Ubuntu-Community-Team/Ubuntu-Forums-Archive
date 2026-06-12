---
title: "Partition gone from table"
date: 2009-08-23
forum: General Help
---

### Post by charrah on 2009-08-23
Installed Windows 7 RC alongside an existing Ubunty Jaunty installation- upon trying to get grub back on, I found that Jaunty's main partition did not exist. It looks like the entry for it just got removed from the partition table, though I'm no expert. I booted a LiveCD and ran fdisk -l and here is the output:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6444    51657728    7  HPFS/NTFS
/dev/sda3            6445        9726    26362665    5  Extended
/dev/sda5            9229        9726     4000185   82  Linux swap / Solaris

```

Supposedly the partition (an ext4) should be between where the extended partition starts and where the swap partition starts. Does anybody have an idea of how to get my partition back?

---

### Post by michy99 on 2009-08-23
I believe that testdisk is able to repair partition tables.

---

### Post by P4man on 2009-08-23
looks to me like windows overwrote your ubuntu ext4 partition?
Can you post a printscreen of what gparted shows ?

---

### Post by charrah on 2009-08-23
Testdisk found my ext4 partition, and the quick search somehow busted the Windows partition(s. Mysteriously in the LiveCD there were... two of them. One was smaller than a GB, don't know what it was for) but for now that isn't a priority; thank you. I was a little worried because the package description mentioned it working with ext2 and ext3 but not ext4; nevertheless it did recognize the partition as being ext4.

@P4man:
The reason I was relatively sure Windows didn't overwrite it was because if you look at the block numbers in the fdisk output, there is a large space in the extended partition between its start and the swap partition, which was where the ext4 partition resided.

---


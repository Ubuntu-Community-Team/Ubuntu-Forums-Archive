---
title: "Recovering EXT4 partition"
date: 2011-12-22
forum: General Help
---

### Post by tommihl on 2011-12-22
Hello,

I accidentally deleted an Ubuntu partition in Windows... I'm unable to rewrite the partition table with testdisk because it only supports EXT3. Any help? I know that its recoverable because I haven't wrote anything over it..

PS. Happy Holidays

---

### Post by searchfgold6789 on 2011-12-22
Testdisk supports ext4:
> TestDisk can 
 
[LIST]
[*] Fix partition table, recover deleted partition
[*] Recover FAT32 boot sector from its backup
[*] Rebuild FAT12/FAT16/FAT32 boot sector
[*] Fix FAT tables
[*] Rebuild NTFS boot sector
[*] Recover NTFS boot sector from its backup
[*] Fix MFT using MFT mirror
[*] Locate ext2/ext3/ext4 Backup SuperBlock
[*] Undelete files from FAT, exFAT, NTFS and ext2 filesystem
[*] **Copy files from deleted FAT, exFAT, NTFS and ext2/ext3/ext4 partitions. **
[/LIST]

That's what I would do: copy all the files to another medium and then use that to recover your system, or restore the data to where it once was.

---

### Post by tommihl on 2011-12-22
> **searchfgold6789 said:**
> Testdisk supports ext4:

That's what I would do: copy all the files to another medium and then use that to recover your system, or restore the data to where it once was.

Okay... Testdisk is saying something like "cannot recover partition" :S

---


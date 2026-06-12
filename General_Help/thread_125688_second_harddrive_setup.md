---
title: "second harddrive setup"
date: 2006-02-04
forum: General Help
---

### Post by psilo357 on 2006-02-04
i have a second harddrive on my computer that i use for storage in windows and  ubuntu, i have the storage partition formatted as FAT32, and i often work with files over 4 gigs.  My question is would it be better to just leave it as is, or convert the partition over to ext2 and use the ext2fs.sys driver for windows?

thanks for the help guys

peace

also....dumb question....but how would i go about formatting those partitions to ext2?

---

### Post by lamego on 2006-02-04
The choice depends on how you intend to use the drive.
If the main use will be on linux I would convert to a ext2 partition.
Anyway FAT32 does not support files greater than 4GB !

You can convert the partition to ext2 using qtparted (install it from the package manager).
Please be aware that the data MUST be erased for this conversion...

---

### Post by taurus on 2006-02-04
mke2fs /dev/hdb1

---

### Post by psilo357 on 2006-02-04
i know that fat32 doesnt support files bigger than 4 gigs, that is why i always have to split them, but dont want to.  When i was windows only, this was no prob as i had it as NTFS, but i use linux for everything other than online gaming, so i guess that ext2 would be the best bet for the other two, i mainly store all my music, files, movies, and whatnot on them, but need to do work on it in both windows and linux.  Also, im kind of new to linux and Ubuntu, so i have no idea what im supposed to do with

mke2fs /dev/hdb1

i need more info, but thanks anyways

peace

---

### Post by taurus on 2006-02-04
You type the comand at the prompt...  Open a terminal and enter the command below!  mke2fs /dev/hdb1 means format the first partition of the second HD as ext2...  And if you want to format it as ext3, then the command looks like

sudo mke2fs -j /dev/hdb1

Otherwise, read the manpage,

man mke2fs

---


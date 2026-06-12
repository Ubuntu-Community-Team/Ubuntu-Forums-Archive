---
title: "df -h gives output"
date: 2012-07-12
forum: General Help
---

### Post by sinnadyr on 2012-07-12
```
Filesystem                Size      Used Available Use% Mounted on

/dev/sdb1               916.9G    890.6G         0 100% /var/media/1tb

```

How is this possible? Available disk space doesn't start counting until there is at least 30G free space, even though I can store data up to 916.9G. 

Thank you

---

### Post by plucky on 2012-07-12
> **sinnadyr said:**
> ```
Filesystem                Size      Used Available Use% Mounted on

/dev/sdb1               916.9G    890.6G         0 100% /var/media/1tb

```

How is this possible? Available disk space doesn't start counting until there is at least 30G free space, even though I can store data up to 916.9G. 

Thank you

What filesystem are you using on the device?

---

### Post by sinnadyr on 2012-07-12
fat32

EDIT: fat32 on system, ntfs on the HD in question

---

### Post by Cheesemill on 2012-07-12
> **sinnadyr said:**
> fat32
 
EDIT: fat32 on system, ntfs on the HD in question
 
Is it FAT32 or NTFS?
It can't be both.

---

### Post by plucky on 2012-07-12
> Is it FAT32 or NTFS?
It can't be both. 

Could be a WUBI install and an external Hard drive.

> How is this possible?

Could be that it wasn't un-mounted correctly and the file system is now dirty.

You could try running a windows file system check and then see if the **df -h** command now sees the correct values.

Good luck

---

### Post by sinnadyr on 2012-07-12
> **plucky said:**
> Could be a WUBI install and an external Hard drive.

Yes, it is an external hard drive, sorry I forgot to mention that. I didn't list all drives in my df to make it easier to read my question. 

How do I do a file system check? Thank you

---

### Post by plucky on 2012-07-12
> How do I do a file system check? 

If you have windows in a dual boot configuration,use that to run a file system check.

Could be just booting into windows and using the **Safely remove drive** will clean up the partition.

If not you can run gparted and run the check from the menu for your ntfs partition.Not sure if this will work as I don't use windows.

Good Luck

---

### Post by sinnadyr on 2012-07-12
Ran check with gparted, worked like a charm. Thank you!

---


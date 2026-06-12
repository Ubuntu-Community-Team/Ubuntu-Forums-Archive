---
title: "Mounting partitions on other hard drives"
date: 2009-08-08
forum: General Help
---

### Post by Gitykins on 2009-08-08
So, I am in /dev/sdb1, and I'd like to mount /dev/sda1. Is this possible?

Probably pretty easy, just not getting it.

---

### Post by SoftwareExplorer on 2009-08-08
Are you trying to do this from the terminal?
I so, could you run```
pwd
```and paste what it says here?
It will help me give you the correct command.

---

### Post by ju2wheels on 2009-08-08
```

sudo mount -t TYPE /dev/sda1 /path/to/mount/folder/

```

if the partition is NTFS use ntfs-3g for TYPE, or if it is FAT16/32 use vfat. For most others you can omit the "-t TYPE".

---

### Post by Gitykins on 2009-08-08
My home directory is /home/neil... but I got it. I was using -t fat instead of -t vfat... thanks.

---

### Post by SoftwareExplorer on 2009-08-08
By the way, welcome to ubuntuforums Gitykins.

---


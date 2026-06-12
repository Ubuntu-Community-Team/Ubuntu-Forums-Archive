---
title: "recovering FF bookmarks"
date: 2010-01-06
forum: General Help
---

### Post by Falc7 on 2010-01-06
Hi
2 Things really. I have two kubuntu installs on my computer, one of them has now stopped booting, it gets to the log in screen, i put my password in, but then the screen flashes black and it returns me to the log in screen again. What i want from this partition is my firefox book marks so i can move them to my new partition. How can i get this?

---

### Post by Barriehie on 2010-01-06
Once logged into the system that does boot can you mount the partition that doesn't boot?  Are both partitions on the same drive?, if so please post your /etc/fstab file.

---

### Post by Falc7 on 2010-01-06
Yes i can mount the non booting partition, and yes they are on the same HDD

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=97da6210-9927-4fb9-9697-8227b4fe0221 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=31d3a103-8f4a-43a5-8c15-b98c5d555b9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by Barriehie on 2010-01-06
Cool!!! FF, on 8.04, stores the bookmarks in ~/.mozilla/firefox/**random letters and numbers for the profile**.default/ and then you're looking for two files: places.sqlite and places.sqlite-journal.  I would get those on the partition that does boot and then create another FF profile to put those two files in unless you don't mind replacing your current bookmarks with those.

---

### Post by Falc7 on 2010-01-06
Thanks that worked :)

---

### Post by Barriehie on 2010-01-06
> **falc7 said:**
> thanks that worked :)

8)

---


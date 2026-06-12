---
title: "uninstall grub after removing ubuntu"
date: 2009-08-25
forum: General Help
---

### Post by konnorrigby on 2009-08-25
Hello all,
 
i installed ubuntu on a 200 gb hdd on a computer that wasnt mine with permision and the owner wants it off.
 
   so without thinking i just booted gparted and cleared ubuntu and swap. but my delema is it still is trying to use grub on dev/sda 5.
 
my old partition layout...
 
```

/dev/sda/
   /dev/sda1/ 
windows recovery   fat32
 
   /dev/sda2/
Windows XP   ntfs
 
   /dev/sda5/
Ubuntu 9.04  ext3  grub is here
 
   /dev/sda6/
linux swap

```
 
my new one...
```

dev/sda/
   /dev/sda1/
windows recovery   fat32
 
dev/sda2/
Windows XP   ntfs

```
 
 
i just want those two partitions.

---

### Post by bmorency on 2009-08-25
do you have a windows xp cd? if you do try this.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")

---

### Post by konnorrigby on 2009-08-26
thank you so much! i got it back up in running.

---


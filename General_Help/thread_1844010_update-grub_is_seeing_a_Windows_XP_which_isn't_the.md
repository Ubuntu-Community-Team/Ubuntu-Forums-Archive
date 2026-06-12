---
title: "update-grub is seeing a Windows XP which isn't there"
date: 2011-09-14
forum: General Help
---

### Post by jemenake on 2011-09-14
Whenever update-grub runs (actually, it's a symlink to update-grub2, I believe), it detects the kernels on my Ubuntu partition, and it finds my Windows XP partition. It **also** finds another partition which it thinks has Windows XP on it. 

It probably had XP on there at one time, but that was long ago. All of the files and folders from any WinXP installation are gone from it. I can only surmise that update-grub is detecting something in the boot sector of that partition or something.

What's the safest way to alter the partition table or boot sector so that update-grub doesn't detect anything there? I was tempted to just use dd to write zeros over the first sector, but some filesystems keep some data in the boot sector, so I didn't want to go that route if I can just change a few bytes in a sector somewhere.

- Joe

---

### Post by Lisiano on 2011-09-14
I think running something equivalent to this should help
```
# dd if=/dev/null of=/dev/sdXX bs=446 count=1
```
Note this code is used to wipe the bootloader from a MBR (eg: sda) but IMO this could be used on a partition, I'm not sure though. If the data can be backed up somewhere safe you can format it to something else. If I have some time I might check if I can run that command on a partition and if it will live. Before that. USE AT YOUR OWN RISK! YOU HAVE BEEN WARNED!

---

### Post by Lisiano on 2011-09-14
So. After putting Ubuntu 11.10 Beta under the virtual knife. It booted (I zeroed sda1). So I guess it could work. But DO create a backup using ```
# dd if=/dev/sdXX of=/some/safe/place/I/MEAN/IT bs=446 count=1
```As before. At your own risk but with no caps.

EDIT: The FS was EXT4

---

### Post by coffeecat on 2011-09-14
You don't need to zero anything. A simple reformat of the offending partition will do the job. Or even some selective deleting of files within it - grub-update is mostly looking for boot files.

But before you zero or reformat anything, I suggest you run the boot script to see exactly what is on your system. It could be that you have an unusual Windows setup spread over two partitions and this is confusing grub-update. Deleting one partition in some circumstances could make Windows unbootable.

Or this might be a recovery partition of some sort with Windows boot files. It might be a recovery partition that you don't want to get rid of.

Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags and we can see what is what.

---


---
title: "dd - device copy.... low file system space"
date: 2011-03-17
forum: General Help
---

### Post by marky1254 on 2011-03-17
So I wanted to copy a copy-protected disk and decided to try dd after reading some information about it. 

after running dd for about a minute, I got a warning that I was low on disk space. I stopped dd and found I had only 200 MB left of 200 GB free space (originally having over 220 free). I deleted the 1/2 finished backups but cannot find the data which was written to the drive. It is hard to think that that much data could be written with my slow pc in under one minute.

here are the commands I performed if that helps locate the data:


dd if=/dev/cdrom of=/mnt/disk/home/mark/pccheck.iso
dd if=/dev/cdrom of=/home/pccheck.iso
sudo dd if=/dev/cdrom of=/home/pccheck2.iso

---

### Post by blueridgedog on 2011-03-17
Start with:

```
cd /
sudo du --max-depth=1 | sort -g
```

From there, you can cd into other directories, as needed, looking for large files.

---

### Post by marky1254 on 2011-06-08
thanks. I think the partition was actually just that small... was screwing around with a shitty computer.. but great to know.

---


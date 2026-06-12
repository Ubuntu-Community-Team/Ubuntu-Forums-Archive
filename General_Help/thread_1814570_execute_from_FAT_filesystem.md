---
title: "execute from FAT filesystem"
date: 2011-07-29
forum: General Help
---

### Post by supereater14 on 2011-07-29
I have a collection of ELF executables that I am trying to run from a FAT filesystem. How can I do this without modifying the OS?
p.s. I am running 11.04

---

### Post by WorMzy on 2011-07-29
FAT (and NTFS) don't support Unix file permissions, so you need to tell the filesystem what to use at mount time. A simple one-off solution would be to mount the filesystem manually, using the mount command with the correct options. e.g.

```
sudo mount -t vfat -o defaults,uid=1000,gid=1000,umask=002 /dev/sd## /mnt
```

uid = user ID (1000 = the first "normal" user, the one you created when you installed)
gid = group ID (same as uid) 
umask = permissions mask (000 = read, write and execute permissions for everyone)

For a more permanent solution, write an fstab entry for the partition in question. You may find that [this tutorial]("http://ubuntuforums.org/showthread.php?t=1604251") helps you with that, if you choose to use it (I wrote it for NTFS, but it will work for fat, so long as you replace "ntfs" with "vfat")

---

### Post by supereater14 on 2011-07-29
that didn't work

---

### Post by WorMzy on 2011-07-29
Any specific reason why?

What's the out of ```
mount
``` say?

---


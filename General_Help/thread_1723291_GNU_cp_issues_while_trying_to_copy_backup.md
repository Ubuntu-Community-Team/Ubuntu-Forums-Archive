---
title: "GNU cp issues while trying to copy backup"
date: 2011-04-06
forum: General Help
---

### Post by stber321 on 2011-04-06
i had many issues and decided to reinstall, i was able to get into the shell
1st i got a list of all packages using "dpkg --get-selections > packages"
then i backed up my home directory using tar, i now have backup.tar.gz
next i mounted an externel hard drive and found it was 400GB
i then used "du -h" to find that backup.tar.gz was 13GB
so i attempted to copy using ```
cp /backup.tar.gz /mnt/hd
```i got "cp: file too large",
please help

---

### Post by galvatron408 on 2011-07-30
you should use rsync

rsync /home/dir /mnt/hd/

---

### Post by dcstar on 2011-07-30
> **stber321 said:**
> i had many issues and decided to reinstall, i was able to get into the shell
1st i got a list of all packages using "dpkg --get-selections > packages"
then i backed up my home directory using tar, i now have backup.tar.gz
next i mounted an externel hard drive and found it was 400GB
i then used "du -h" to find that backup.tar.gz was 13GB
so i attempted to copy using ```
cp /backup.tar.gz /mnt/hd
```i got "cp: file too large",
please help

Using FAT formatted drives, eh?

---


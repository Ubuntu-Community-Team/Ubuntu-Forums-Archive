---
title: "Directory is evading deletion."
date: 2009-08-11
forum: General Help
---

### Post by aronstandley on 2009-08-11
There are a few files that are taking up huge amounts of space on my tiny Eee. Each file is multiple gbs, and none of them are part of the systems files. They've been placed into a directory that I put into my removable SSD.

Each file has a name that is composed of characters that would do the 133t artists proud: boxes with "0004", "0014" written within, lines, umlauted 'a's, Black squares...

Suffice to say, I would like these files deleted, but have been unable to find a way to do this.

"sudo rmdir" got me
```
rmdir: failed to remove /directory/location : Read-only file system
```sudo shred -f -v -z -u got me
```
failed to open for writing: Is a directory
```

gksudo nautilus got me an error while deleting
> Error stating file '/directory/location/crazy-character filename': Input/output error
What is to be done? How may this situation be remedied?

---

### Post by michy99 on 2009-08-11
What do you get from these commands?```
ls -ld /directory/location
lsattr /directory/location
```

---

### Post by jaxxstorm on 2009-08-11
try
```
 rm -rf directoryname
```

I feel obliged to warn you that this command is dangerous, so ensure you're deleting the right directory before you proceed with hitting enter.

If it still doesn't work, try sudoing it.

---

### Post by dcstar on 2009-08-12
> **aronstandley said:**
> There are a few files that are taking up huge amounts of space on my tiny Eee. Each file is multiple gbs, and none of them are part of the systems files. They've been placed into a directory that I put into my removable SSD.

Each file has a name that is composed of characters that would do the 133t artists proud: boxes with "0004", "0014" written within, lines, umlauted 'a's, Black squares...

Suffice to say, I would like these files deleted, but have been unable to find a way to do this.

"sudo rmdir" got me
```
rmdir: failed to remove /directory/location : **Read-only file system**
```
......

Unmount the filesystem, do a fsck on it and then remount it.

---


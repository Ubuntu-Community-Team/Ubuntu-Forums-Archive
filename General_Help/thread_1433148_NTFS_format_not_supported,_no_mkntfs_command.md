---
title: "NTFS format not supported, no mkntfs command"
date: 2010-03-18
forum: General Help
---

### Post by 98cwitr on 2010-03-18
getting this error

"Error creating file system: helper exited with exit code 1: cannot spawn 'mkntfs -f -L "Backup" /dev/sdb1': Failed to execute child process "mkntfs" (No such file or directory)"


tried to run from terminal and mkntfs is not in the system. I am trying to make an image of my system using dd and its over 4GB.

---

### Post by sandyd on 2010-03-18
```

sudo apt-get install ntfs-3g libntfs10 ntfsprogs
```

---

### Post by 98cwitr on 2010-03-18
and that did it...thank you sir. Didnt have the libntfs10 installed.

---


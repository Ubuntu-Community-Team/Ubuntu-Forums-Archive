---
title: "Fstab configuration"
date: 2011-01-16
forum: General Help
---

### Post by travisl_10 on 2011-01-16
Hello, I edited fstab so that my Windows disk partition will be automatically mounted when I log on. However, when I delete a file from said partition, I am told that the item(s) cannot be moved to trash - I can only permanently delete files from the Windows partition.

Here is how I configured in fstab:
```

/dev/sda1  /media/Vista  ntfs  nls=iso8859-1,umask=000  0  0 

```

I suspect I mis-configured the options. Can anyone see an issue? Help would be greatly appreciated.

---

### Post by oldos2er on 2011-01-17
Answer in post #2 here: [http://ubuntuforums.org/showthread.php?t=1499345](http://ubuntuforums.org/showthread.php?t=1499345)

---


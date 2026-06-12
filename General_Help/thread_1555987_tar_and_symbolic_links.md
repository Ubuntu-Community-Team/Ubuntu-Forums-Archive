---
title: "tar and symbolic links"
date: 2010-08-18
forum: General Help
---

### Post by jim_deadlock on 2010-08-18
I'm backing up my whole system to an external hard drive using tar and  for the most part it works like a charm. However, I'm having trouble  extracting symbolic links from the tarball, they are restored as empty  files without any permissions or original ownership:

```
$ ls -l /home/jim/mysymlink
lrwxrwxrwx 1 jim  jim     22 2010-08-19 00:18 /home/jim/mysymlink -> /media/Maxtor/mysymlink

$ sudo tar cfpz /media/Maxtor/backup1.tgz --exclude=/media/Maxtor /

$ sudo tar xfpz /media/Maxtor/backup1.tgz home/jim/mysymlink

$ ls -l /home/jim/mysymlink
---------- 1 root root     0 2010-08-19 00:19 /home/jim/mysymlink
```

All other files can be extracted properly with correct ownership/permissions, it's only symbolic links I'm having the problem with. Any ideas?

---


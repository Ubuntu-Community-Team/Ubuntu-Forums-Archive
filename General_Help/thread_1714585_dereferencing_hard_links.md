---
title: "dereferencing hard links"
date: 2011-03-25
forum: General Help
---

### Post by w_barnes on 2011-03-25
How do I dereference a hard link? I know I can use stat to show the number of hard links for a given file but I would to be able to see a list of files that are hard linked to the same data. If there is no way to dereference directly, how about searching the file system for all files that have the same inode?

---

### Post by sisco311 on 2011-03-25
```
find /path/to/dir -xdev -samefile filename
```

---

### Post by w_barnes on 2011-03-25
Thanks! That's exactly what I was looking for =D>

---

### Post by sisco311 on 2011-03-25
You're welcome!

You can also use **-inum n** to search for a file with an inode number n and if you use the -L option, find will print the symlinks as well. All this options are well documented in find's man page.

---


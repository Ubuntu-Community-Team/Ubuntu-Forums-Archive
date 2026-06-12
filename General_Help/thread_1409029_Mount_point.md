---
title: "Mount point"
date: 2010-02-17
forum: General Help
---

### Post by royale1223 on 2010-02-17
What is a mount point(for a partition)? How can I create it?

---

### Post by chewearn on 2010-02-17
Linux system has a single directory tree containing everything.  This is different from e.g. Windows system, where there are multiple directory trees, one for each drive letter.

A mount point of a partition, is where the partition get "attached" to the directory tree.

You create a mount point the same way you create a directory.  Via GUI, right-click, "Create Folder", or via command line:
```
mkdir directory
```

Once the directory is created, you use "mount" command to "attach" the partition.

---


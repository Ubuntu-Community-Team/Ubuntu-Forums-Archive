---
title: "Moving files and leaving links behind"
date: 2009-12-21
forum: General Help
---

### Post by samuelhug on 2009-12-21
Hi I was wondering if anybody knows of a way to move a file that is being written to at the same time and leave a sym link pointing to the new location for the app writing to the file.

When my Firefox plugin starts downloading a file into the /tmp directory I would like to be able to move the file some where else without waiting till it finishes.

---

### Post by dcstar on 2009-12-22
> **samuelhug said:**
> Hi I was wondering if anybody knows of a way to move a file that is being written to at the same time and leave a sym link pointing to the new location for the app writing to the file.

When my Firefox plugin starts downloading a file into the /tmp directory I would like to be able to move the file some where else without waiting till it finishes.

Why not just get Firefox to prompt you to put the file where you actually want it?

---

### Post by geirha on 2009-12-22
If it's on the same filesystem, you can move a file while its being written to, and it will not interrupt the writing. A filename itself is just a link (hardlink) to the file's inode, and the hardlink is only needed when opening the file, to find the right inode.

---

### Post by samuelhug on 2009-12-22
Wow thanks geirha I can't believe it was that simple.

---


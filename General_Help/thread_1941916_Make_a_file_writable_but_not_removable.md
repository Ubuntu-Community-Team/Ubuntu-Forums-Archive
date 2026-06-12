---
title: "Make a file writable but not removable"
date: 2012-03-16
forum: General Help
---

### Post by Cadeyrn on 2012-03-16
I'm affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/cellwriter/+bug/935277](https://bugs.launchpad.net/ubuntu/+source/cellwriter/+bug/935277)

It seems nothing is being done to fix it, and it's so ridiculously annoying that I can't wait around for it to be fixed. I want to make ~/.cellwriter/profile impossible to delete by anyone except root, but it still needs to have read/write permissions for my user because it's a settings file. Is there any way to do this?

---

### Post by vamped on 2012-03-16
Well that seems impossible, but i just did a quick test that seems promising:

Create a directory. Create a file in that directory. Remove write permissions from the directory. You can change the file, but not delete it. You cannot create or remove files from the directory, but it seems you can change an existing file.

---

### Post by Cadeyrn on 2012-03-16
That worked. Thanks!

---


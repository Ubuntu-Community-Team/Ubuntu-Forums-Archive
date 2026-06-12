---
title: "Ordered Data Recovery"
date: 2009-10-16
forum: General Help
---

### Post by lajevardi on 2009-10-16
Hi,
I've just deleted my home directory data recursively via `rm -R` command. The data is now recovered massively using PhotoRec saviour tool in  bunch of unordered folders. 
But since the data in the home directory is used by applications for storing data, I think it's important for data to be recovered in the same old order & hierarchy.
Any idea?
thanks.

---

### Post by Giblet5 on 2009-10-16
Never heard of it.

This's why the "tar" and "cpio" commands have been included with Unix-like systems since the late 70's. They just work.

Rsync is good too.

Or, you can set up LVM and take snapshots while people are using the system.

As for your current issue, you probably need to dig through that software's documentation and see how to recover preserving the original directory tree.

---

### Post by lajevardi on 2009-10-16
I think, I didn't justify you by explaining the issue well in the previous post.
Some data is **accidentally** removed, no copies available and I don't understand that how the *tar* or *cpio* archive commands, or LVM snapshots could help on this! thanks ;)

---

### Post by lajevardi on 2009-10-16
Ok then,
I'll let it go! rebooting as soon as I end this up and setting all applications configuration data again.

---


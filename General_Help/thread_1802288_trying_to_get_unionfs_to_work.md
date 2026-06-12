---
title: "trying to get unionfs to work"
date: 2011-07-11
forum: General Help
---

### Post by Skaperen on 2011-07-11
While reading this:

[http://manpages.ubuntu.com/manpages/lucid/en/man4/unionfs.4.html](http://manpages.ubuntu.com/manpages/lucid/en/man4/unionfs.4.html)

I tried to get a unionfs test scenario to work.  The error message says:

```
mount: unknown filesystem type 'unionfs'
```So I found package "unionfs-modules" and tried to install it.  I got:
```
maxwell/root/fs1 /root 11# apt-get install unionfs-modules
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package unionfs-modules is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unionfs-modules has no installation candidate
maxwell/root/fs1 /root 12#
```Do I need the "unionfs-fuse" package for this?  I thought it was a kernel module.

---


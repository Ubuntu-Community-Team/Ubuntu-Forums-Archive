---
title: "Dynamic inode filesystem"
date: 2011-12-16
forum: General Help
---

### Post by curmudge1 on 2011-12-16
We're having a problem where we run out of Inodes way before we run out of disk, as we have an application that has a lot of small files and a relatively high number of directory levels.

So, we need a filesystem for our Ubuntu servers that dynamically allocates inodes.  We're mostly using Ubuntu 11.04.

Would like something like ZFS, or Vxfs (Veritas).   Has anyone used Veritas file system on Ubuntu, successfully?

Thanks for any help.

--
David Strom

---

### Post by dcstar on 2011-12-17
> **curmudge1 said:**
> We're having a problem where we run out of Inodes way before we run out of disk, as we have an application that has a lot of small files and a relatively high number of directory levels.

So, we need a filesystem for our Ubuntu servers that dynamically allocates inodes.  We're mostly using Ubuntu 11.04.

Would like something like ZFS, or Vxfs (Veritas).   Has anyone used Veritas file system on Ubuntu, successfully?

Thanks for any help.

--
David Strom

Why not just create the EXT filesystem with more inodes than the default?

---

### Post by curmudge1 on 2011-12-19
dcstar -- looks like that's what I will have to do.   Problem is, I don't *know* how many we'll need, this is a filesystem that our people are adding to all the time.   So, I may wind up doing this over & over again.

XFS turns out to be a real DOG!  I tried cp -R to copy 72GB starting Friday afternoon, and Monday morning ~8:45am, only 38GB was copied.  (<sigh>)  So, XFS is out.

Might put up a Solaris vm with ZFS, and NFS share this data.

---

### Post by LewisTM on 2011-12-19
Why not go with Btrfs? It's supported in Ubuntu and will soon become the default fs. It has similar features as ZFS and  dynamically allocates inodes.

---


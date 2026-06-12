---
title: "why cant I browse my files using remote file system?"
date: 2010-02-14
forum: General Help
---

### Post by ayet on 2010-02-14
I am new to XUbuntu and I cant seem to browse my other hard drives connected to my system, It keep saying Connecting to "60 GB Filesystem" failed.Authentication is required.
how do I browse my other hard drives in Xubuntu?

---

### Post by jocko on 2010-02-14
I'm not sure why the title says "remote file system" when the rest of the post seems to be about local hard drives...
But if the problem is that you can't access your local, internal hard drives I think I can help.

A file system needs to be mounted before you can browse it, but the os can be set up to mount a file system automatically when it starts.

First you need to provide a little bit of information about your system.
Open up a terminal and type or copy/paste these commands one at the time into it:
```
cat /etc/fstab
sudo fsdisk -l
sudo blkid
```
Copy the output of each of those commands into a post here, and I or someone else will tell you what to do to get your hard drives/partitions mounted automatically.

---


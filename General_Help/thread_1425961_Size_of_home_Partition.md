---
title: "Size of /home Partition"
date: 2010-03-09
forum: General Help
---

### Post by Gias Kay on 2010-03-09
Hi all,

What's the size of your /home partition? I'm thinking about 1~2 GB, but then there is Wine's C drive. Is it good to move the C drive folder on another partition and pointing to it with a symbolic link?

---

### Post by dcstar on 2010-03-09
> **Gias Kay said:**
> Hi all,

What's the size of your /home partition? I'm thinking about 1~2 GB, but then there is Wine's C drive. Is it good to move the C drive folder on another partition and pointing to it with a symbolic link?

Are you somehow desperately short of disk space?

---

### Post by nothingspecial on 2010-03-09
> **Gias Kay said:**
> Hi all,

What's the size of your /home partition? I'm thinking about 1~2 GB, but then there is Wine's C drive. Is it good to move the C drive folder on another partition and pointing to it with a symbolic link?

Your / partition should be somewhere between 2 and 8 gigs depending on your linux distribution.

Your /home partition should be whatever else is left - (assuming you don`t have other /boot, /opt ,/var etc partitions)

---

### Post by lovinglinux on 2010-03-09
> **Gias Kay said:**
> Hi all,

What's the size of your /home partition? I'm thinking about 1~2 GB, but then there is Wine's C drive. Is it good to move the C drive folder on another partition and pointing to it with a symbolic link?

I do that. My home partition has only 8 Gb to store config files and temporary stuff. All my personal files and folders are symlinked from other partitions. I also symlink .wine and .Virtualbox, since they are big. Works like a charm.

I don't recommend using only 2 Gb, since you could end up without space, even with symlinks. I'm currently using 600 Mb of 8Gb, but I like to temporarily save some stuff in the Desktop, which I haven't symlinked (not sure if it is a good idea to symlink the Desktop).

---


---
title: "permission denied when trying to append to file"
date: 2011-02-07
forum: General Help
---

### Post by yawnmoth on 2011-02-07
sudo echo fuse >> /etc/modules

Any idea why that'd yield a "bash: /etc/modules: Permission denied" error?  Here's what "stat /etc/modules" says:

```
  File: `/etc/modules'
  Size: 207       	Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d	Inode: 3670461     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2011-02-07 22:20:54.094067890 -0600
Modify: 2011-02-07 22:21:12.994067893 -0600
Change: 2011-02-07 22:21:12.994067893 -0600
```

---

### Post by dcstar on 2011-02-08
> **yawnmoth said:**
> sudo echo fuse >> /etc/modules

Any idea why that'd yield a "bash: /etc/modules: Permission denied" error?  ..........

[http://ubuntuforums.org/showpost.php?p=3642580&postcount=7](http://ubuntuforums.org/showpost.php?p=3642580&postcount=7)

---


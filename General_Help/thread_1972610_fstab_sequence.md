---
title: "fstab sequence"
date: 2012-05-03
forum: General Help
---

### Post by yeahimthatguy on 2012-05-03
Hello,

I ran into a problem working with fstab file. 

I had several entries on it to mount NFS share, then create a bind mount from that NFS mount. Looking at the log, it appears that when you try to bind mount the NFS mount, it doesn't see it.

Yet, after it has booted up and I issue a mount -a command, it can mount that drive without any issues.

I also read that if SELinux is enabled, you can't mount to the home directory, but I would think that you would get a different error other than that the path of the bind mount source cannot be found.

My thought was perhaps it's mounting not in the order of the entry so it's not there yet.

Any help will be greatly appreciated.

Thanks.

---


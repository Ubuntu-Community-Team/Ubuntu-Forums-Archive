---
title: "vm.vfs_cache_pressure"
date: 2009-08-16
forum: General Help
---

### Post by s3a on 2009-08-16
What are the pros and cons of a vm.vfs_cache_pressure=50 value vs a vm.vfs_cache_pressure=100 value?

Any input would be appreciated!
Thanks in advance!

---

### Post by vaerer on 2009-08-16
I was just about to ask this question,

you beat me to it though :P

[COLOR=Gray](and considering my luck getting answers, maybe it's better that you asked)[/COLOR]

---

### Post by Kangarooo on 2011-11-08
im also interested

---

### Post by Csimbi on 2012-09-05
Found this:
> Controls the tendency of the kernel to reclaim the memory which is used for caching of directory and inode objects.  At the default value of vfs_cache_pressure=100 the kernel will attempt to reclaim dentries and inodes at a "fair" rate with respect to pagecache and swapcache reclaim.  Decreasing vfs_cache_pressure causes the kernel to prefer to retain dentry and inode caches. When vfs_cache_pressure=0, the kernel will never reclaim dentries and inodes due to memory pressure and this can easily lead to out-of-memory conditions. Increasing vfs_cache_pressure beyond 100 causes the kernel to prefer to reclaim dentries and inodes.[Here]("http://www.kernel.org/doc/Documentation/sysctl/vm.txt").
More info [here]("http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that").
Some feedback [here]("http://ubuntu.5.n6.nabble.com/Re-Excessive-swapping-with-1GB-of-memory-UBUNTU-12-04-daily-build-td4918049.html").

---


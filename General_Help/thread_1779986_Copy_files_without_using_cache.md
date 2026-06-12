---
title: "Copy files without using cache"
date: 2011-06-11
forum: General Help
---

### Post by qvx on 2011-06-11
I understand that linux kernel very aggressively caches files. The result of that is when you copy a large amount of data/files (using `cp` or `nautilus`) all your RAM is used at the expense of other running programs even to the point that your active programs are removed from memory and put to swap area.

I was copying backups from local disk to external USB (over a million of files, around 150GB). The operation took over an hour and in the meantime the computer was completely unusable. You could not scroll inside gvim, open a page in firefox and so on.

I have found the following resources, but none of them resolves the issue, only explains it:

[LIST]
[*] [http://ubuntuforums.org/showthread.php?t=895246]("http://ubuntuforums.org/showthread.php?t=895246") -- Similar discussion to this one
[*] [http://duopetalflower.blogspot.com/2009/09/clearing-cache-memory-in-linux-using.html]("http://duopetalflower.blogspot.com/2009/09/clearing-cache-memory-in-linux-using.html") -- How to manually clean the cache ```
sudo sync && sudo sysctl -w vm.drop_caches=3 && sudo sysctl -w vm.drop_caches=0 
```
[*] [http://ubuntuforums.org/showthread.php?t=489719]("http://ubuntuforums.org/showthread.php?t=489719") -- Mention that you can use `dd` to copy without caching files, but it cannot be used to copy entire directories or to `tar` the files: ```
dd iflag=direct,nonblock if=b_1_GB_file bs=64k oflag=direct,nonblock of=b_1_GB_file.backup
```
[*] [http://insights.oetiker.ch/linux/fadvise.html]("http://insights.oetiker.ch/linux/fadvise.html") -- Explains how one could enhance `cp` or `tar` so as not to use file caching. It consists of calling ```
posix_fadvise(fd,0,0,POSIX_FADV_DONTNEED);
``` on your file descriptors.
[/LIST] 

I have nothing against file caching, it makes my box snappy, but there are cases when it behaves extremely bad. I don't expect kernel to adopt a new policy, but a way to manually circumvent such behaviour when needed.

For example:
[LIST]
[*] Patch to existing utility: `cp --no-cache`
[*] Limit cache memory: i.e. `limit_file_cache 100M`. Good because other programs could continue to work unchanged, but still, other *useful* file caches (like open vi files) would be invalidated with large copy operation.
[*] Entirely disabling cache during copy would probably have undesirable effects on the rest of the system so it is a "no solution".
[/LIST]

I hope that I'm missing some existing utility or option which would allow me to copy files without thrashing my PC.

--
Tvrtko

---

### Post by qvx on 2011-06-12
I've done some tests and here is the update.

The real culprit was actually Nautilus. It consumed around 2GB of private process memory while copying data (memory leak and/or a list of files to be copied). Nautilus scans a directory structure for all the files to be copied and most probably stores the list in memory. When you have more than million files, such list takes a lot of real memory space. After a copy was done, none of that memory was released (memory leak?). I had to kill nautilus. Dolphin/Krusader behave similarly as Nautilus (take around 2GB of ram for file lists).

`cp` behaves much better. It copies a directory structure blindly and takes less than 1MB total to perform the copy. The cache is still filled and all other useful files are removed from cache, but that is mostly OK; at least memory from other running programs is not swapped out.

---


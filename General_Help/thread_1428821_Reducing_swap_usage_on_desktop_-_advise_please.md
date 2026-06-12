---
title: "Reducing swap usage on desktop - advise please"
date: 2010-03-13
forum: General Help
---

### Post by madwoollything on 2010-03-13
I have a netbook and one of the suggested optimizations was to reduce the use of swap

[B]Optimizing the Kernel

Add the following to your /etc/rc.local file.
# Economize the SSD
sysctl -w vm.swappiness=1 # Strongly discourage swapping
sysctl -w vm.vfs_cache_pressure=50 # Don't shrink the inode cache aggressively

[/B]I've noticed on my desktop and conventional laptop that it is quite usual for the swap file to be used even when memory usage is low (25% of available memory).

I'm looking for some advise on the best way to set up a conventional desktop or laptop as my understanding is that the use of a swap file will slow the system responsiveness down. Can I use a version of the above to improve performance and reduce swap usage?

I've found the following[ https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq") but wondered what has worked for others and what cache_pressure does?

---

### Post by rnerwein on 2010-03-13
hi
you can use vm.swapiness and vm.vfs_cache_pressure.
the value wich is given for swapiness means --> hey system start to use your swap when your free
ram is going down the value you have given ( eg. swapiness=10 --> means under 10% ).
but there is the other value: vfs_cache_pressure. this value the system the percentage to use caching
instead of swaping. the default is 100 and i prefere to let it there because caching for dentries and 
inodes is much faster than swaping.
last at least set swapiness to 10 and don't touch the vfs_cache_pressure.
ciao

---

### Post by madwoollything on 2010-03-13
> **rnerwein said:**
> hi
you can use vm.swapiness and vm.vfs_cache_pressure.
the value wich is given for swapiness means --> hey system start to use your swap when your free
ram is going down the value you have given ( eg. swapiness=10 --> means under 10% ).
but there is the other value: vfs_cache_pressure. this value the system the percentage to use caching
instead of swaping. the default is 100 and i prefere to let it there because caching for dentries and 
inodes is much faster than swaping.
last at least set swapiness to 10 and don't touch the vfs_cache_pressure.
ciao

Thanks :)

---


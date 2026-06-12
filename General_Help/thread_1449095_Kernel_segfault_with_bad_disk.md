---
title: "Kernel segfault with bad disk"
date: 2010-04-07
forum: General Help
---

### Post by mmorgan27 on 2010-04-07
I'm getting repeating messages in /var/log/kern.log:

kernel: [338989.299818] b64[21010]: segfault at 7fff4e424000 ip 0000000000400789 sp 00007fff4e4231b0 error 6 in b64[400000+1000]
kernel: [339370.050078] b64[21085]: segfault at 7fff5a41a000 ip 0000000000400789 sp 00007fff5a418bd0 error 6 in b64[400000+1000]

I'm guessing some component of the kernel is receiving a segfault due to a bad disk.  It hangs when reading certain files from that disk.

Can anyone confirm that this message is due to a disk read action?  The segfault address and stack pointer are inconsistent.  How do I determine which kernel module is mapped (was mapped) to a given address?

Thanks! 
Ubuntu 9.10 64bit

---


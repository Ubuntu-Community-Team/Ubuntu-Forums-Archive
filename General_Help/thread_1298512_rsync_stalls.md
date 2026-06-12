---
title: "rsync stalls"
date: 2009-10-22
forum: General Help
---

### Post by Peneus on 2009-10-22
Hi,

I want to check if somone else has this problem. I have a laptop at home and a pc at work. both hve the same setup: Ubuntu 9.04 (current) with ext4 file system and  rsync 3.0.6 I usually sync them using rsync. But a lot of times I will start rsync and it stalls. I have to run rsync several times to sync my files.  This wasn't a problem on my previous systems. I was wondering if this is a problem with ext4 or rsync. 
If you had the same problem and solved it could you let me know how please.

Thanks a lot.

---

### Post by HermanAB on 2009-10-22
Yes, it appears to me that rsync suffers a deadlock situation under certain situations.  It can usually be prevented with careful use of the BW parameter.  See the rsync man page for details.  Restricting the bandwidth and slowing rsync down a little seems to make it proceed without getting its balls in a twist.

---


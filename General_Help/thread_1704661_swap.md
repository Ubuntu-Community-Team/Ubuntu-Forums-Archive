---
title: "swap"
date: 2011-03-11
forum: General Help
---

### Post by dsupriya on 2011-03-11
Dear all,

I have a desktop workstation with 4 GB RAM. Very soon I'm going to add another 4GB. Now if I install OS now, how much "swap" memory should I create? Can already create 10GB swap required for 8 GB RAM ([http://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-swap-what-is.html](http://www.centos.org/docs/5/html/5.1/Deployment_Guide/s1-swap-what-is.html)) now?

Thanks.

---

### Post by bwang on 2011-03-11
Of course you can; nothing bad will happen.
Its unlikely you'll ever start swapping with 4/8GB RAM anyway.

---

### Post by dsupriya on 2011-03-11
Thanks! But I did not get your second statement.

---

### Post by idoitprone on 2011-03-11
[http://www.cyberciti.biz/tips/linux-swap-space.html](http://www.cyberciti.biz/tips/linux-swap-space.html)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The reason why we need swap is for two reasons- in case to full ram and hibernation. As bwang mention, it is unlikely u will use the full 8 gb of ram, if you manage to do that, a process get move to swap. For hibernation, it is essential, that u have more free swap than the ram u are using. If you are paranoid, just use 8gb of swap as explained in the cyberciti link. Read the ubuntu faq for a better explanation, since i am sometimes hard to understand

---

### Post by Hakunka-Matata on 2011-03-11
Rule of thumb is drive swap partition should be about 2 X RAM.  Place your swap partition at the very end of the drive for best performance.

---


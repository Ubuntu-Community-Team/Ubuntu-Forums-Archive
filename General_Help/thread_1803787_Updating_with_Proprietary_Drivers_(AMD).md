---
title: "Updating with Proprietary Drivers (AMD)"
date: 2011-07-13
forum: General Help
---

### Post by kaldor on 2011-07-13
I recently bought a new PC and it has an AMD GPU. I've been using Catalyst because the open source radeon driver gave me poor performance in games (maybe by 12.04 I can use it :( ).

I've had some updates show up recently. This brings me to wonder if I have anything at all to worry about. This is a production machine and I don't want to muck around with fixing issues brought on by my usual *apt-get upgrade*.

Currently, I've been avoiding updating a few packages related to the Kernel and Xorg:

```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  linux-libc-dev xserver-xorg-video-ati xserver-xorg-video-radeon
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

I had an NVIDIA issue back on Ubuntu 8.04 after updating once, due to a kernel update. I had to revert to an older kernel and mess around a bit to fix my installation. I don't have any experience with Catalyst. 

Basically, I want input as to whether or not it's dangerous to update this sort of stuff. I don't want to mess around fixing issues caused by a rogue update ;)

Ubuntu 11.04 64 bit
AMD Radeon HD 6450
Latest proprietary driver available from Jockey.

Thanks :)

---

### Post by macaholic on 2011-07-14
In my experience recently (with both nvidia and AMD), proprietary graphics updates and kernel updates have very rarely caused any malfunctions that make the machine unusable. If anything, there will be performance regressions, but the functionality will almost certainly remain intact. It would be my suggestion to keep up with the official updates.

---


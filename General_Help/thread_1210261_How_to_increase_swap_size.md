---
title: "How to increase swap size?"
date: 2009-07-11
forum: General Help
---

### Post by uv2008 on 2009-07-11
Hello all. I'm using Ubuntu 9.04 64 bit, having 3.8GB memory and 1.8GB swap. I'm using an application that requires a huge amount of memory - about 7GB-8GB, so I need to increase my swap size. Any idea how to do that without risking my other partitions?
Thanks for any idea!

---

### Post by nice_like_rice on 2009-07-11
Use gparted ("sudo gparted"), and downsize one of your other partitions, then increase the size of the swap partion, and apply the changes.

---

### Post by carml on 2009-07-11
I would do as the user before me said,using instead a Live cd of Ubuntu or Gparted Live,because partitions should to be unused when one want to resize them,so boot with one of the cd I suggested before. :)

---


---
title: "How to Pool multiple drives into a single filesystem"
date: 2012-06-29
forum: General Help
---

### Post by sloany on 2012-06-29
I have 4 hard drives each with a partition each, but I'd like to pool these into a single filesystem.

I've looked into raid/LVM but these are more complex than I need.
I looked into aufs but I read that overlayfs will eventually replace it.

I can't find many examples on using this so I'm wondering if anyone else has pooled multiple (more than 2) partitions using overlayfs, or something else?

Thanks

---

### Post by rubylaser on 2012-06-29
If you just want dead simple pooling, I'd suggest [mhddfs]("http://romanrm.ru/en/mhddfs").  It takes about 2 minutes to setup, and it's dead simple.

---

### Post by sloany on 2012-06-29
> **rubylaser said:**
> If you just want dead simple pooling, I'd suggest [mhddfs]("http://romanrm.ru/en/mhddfs").  It takes about 2 minutes to setup, and it's dead simple.
I also looked into that, but it had performance issues when compared to the others because it has FUSE overheads. I only have an atom cpu running my box so I'd prefer something light weight.

---

### Post by sloany on 2012-06-29
Actually I just gave mhddfs a quick go and it works pretty well, better than I thought it might :)

---


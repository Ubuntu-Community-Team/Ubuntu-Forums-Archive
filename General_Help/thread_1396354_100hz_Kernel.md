---
title: "100hz Kernel"
date: 2010-02-01
forum: General Help
---

### Post by NightwishFan on 2010-02-01
This topic has probably been done to death... However I cannot seem to find a straight answer anywhere I search.

Ubuntu Desktop on AMD64 uses a 100hz kernel with pre-emption. I read that the HZ does not matter much with the way the kernel is configured. I still wondered if it would have a negative effect with latency in online play where timing is essential (first person shooter, etc). I doubt it, but 1000hz/rt is always recommended to me.

Does anyone know for sure? Because the 100hz kernel seems to perform a lot better than a 1000hz one, but I do not know about latency wise.

---

### Post by PoHandle on 2010-02-24
Personally, I use a -rt kernel, and I've noticed that my system is more responsive and 'snappy' that if I use the default 100Hz kernel.  I did notice a decrease in lag (network and input) when playing ETQW with realtime kernel.

I don't know if this is a straight answer, but it's my personal experience.

---

### Post by NightwishFan on 2010-02-24
Thanks for the response.

I have found out that Lucid (10.04) will include a preempt kernel. It is essentially the generic kernel except it has a 1000hz timer and voluntary preemption. I think that would offer better performance than the dedicated "realtime" kernel, which is designed to meet deadlines. I tried it from the alpha and it seems good so far.

[http://www.phoronix.com/scan.php?page=news_item&px=Nzg5Mw](http://www.phoronix.com/scan.php?page=news_item&px=Nzg5Mw)

---


---
title: "Super Slow USB Throughput After Natty Update. Anybody Else??"
date: 2011-07-07
forum: General Help
---

### Post by sjuranic on 2011-07-07
I accepted the latest Natty update about which I was notified a couple of days ago (I don't remember exactly).  I don't remember a new kernel being pushed out, but for the record I'm on 2.6.38-8-generic right now.  I'm trying to interact with a USB compact flash reader and I'm getting ridiculously low throughput (less than 1 MB per second).  Before this latest upgrade, I don't remember this being a problem.

I'm just wondering if anybody else is seeing this?  Better yet, does anybody know what might be wrong and what I might be able to do to fix this?

---

### Post by wojox on 2011-07-07
Is it the same port you used before? There's a mighty big difference in USB 1.1 and 2.0 controller transfer rates. What does  this tell you:

```
lsusb -t
```

---

### Post by wojox on 2011-07-08
You can also look in Ubuntu Software Center and on the left choose History and it will show you what got updated for that day.

---


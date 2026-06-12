---
title: "Network drive: Ubuntu &amp; OSX report different sizes?"
date: 2011-01-01
forum: General Help
---

### Post by PartisanEntity on 2011-01-01
Hi all,

My Ubuntu machine and my iMac report different amounts of free space on a network drive.

The network drive is connected to my Ubuntu machine and is being shared on the network.

Ubuntu report 490GB free.

OSX reports 526GB free.

Any ideas what could be causing this?

---

### Post by solar george on 2011-01-01
Thats due to the differece between how ubuntu and osx define one GB (see [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)). In actual fact ubuntu should be labling that as 490GiB (and I think it will do soon if the latest version doesn't already).

Since 1GiB = ~1.074 GB and 490*1.074 = 526 they are both reporting the same thing.

---

### Post by PartisanEntity on 2011-01-01
Right I see, thanks very much!

---


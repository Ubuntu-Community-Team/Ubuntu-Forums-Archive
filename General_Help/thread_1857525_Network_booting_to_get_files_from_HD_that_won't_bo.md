---
title: "Network booting to get files from HD that won't boot"
date: 2011-10-10
forum: General Help
---

### Post by CavemanJoe on 2011-10-10
So my wife's laptop died, and the new one arrived today.  We want to get all the files from her old machine onto her new one.  Here's what we have:

One dual-boot laptop, Windows XP and Ubuntu 10.04, with optical drive and SATA hard drive (my machine).

One Windows 7 laptop, with optical drive and SATA hard drive (my wife's new machine).

One IDE laptop hard drive containing Windows XP and my wife's data.

One IDE-capable laptop with **no optical drive** and **no usb-boot ability**.

When the IDE drive is installed in the only remaining available IDE laptop, Windows won't boot.  It won't even *nearly* boot.  So, it's a hard drive full of data, but it's essentially got no operating system.

So, we're trying to gain access to the data on this hard drive via a network crossover cable.  The laptop in which the hard drive is installed is PXE-capable.

Does anybody have a straightforward guide on how to do that?

---

### Post by TeoBigusGeekus on 2011-10-10
No idea, but you could consider something like [this]("http://www.bixnet.com/usbporenfor2.html").
After copying the data, you'll be left with an extra external hd.

---


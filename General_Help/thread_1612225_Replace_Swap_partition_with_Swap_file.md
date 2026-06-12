---
title: "Replace /Swap partition with Swap file?"
date: 2010-11-02
forum: General Help
---

### Post by mishathegoat on 2010-11-02
Hello everyone,
I currently have Ubuntu Desktop 10.10 installed and have a great setup. However, I'm trying to install another OS on the hard drive and need to remove a partition. I've read online that I can remove the Swap partition and use a "Swap file". My question is this:

Is it possible to replace the Swap partition with a "swap file" without having to re-install linux? And if so, how do I accomplish this? 


Dual-booting: Mac OS X 10.6.3 / Ubuntu Desktop 10.10
Macbook Pro 6,1
2.8 GHz Intel Core i7, 4 GB RAM

Any help is appreciated.

Thanks,
Misha

---

### Post by MooPi on 2010-11-02
I'm currently using a swap file, created with instructions from this page [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
Nice horns :)

---

### Post by dcstar on 2010-11-03
> **mishathegoat said:**
> Hello everyone,
I currently have Ubuntu Desktop 10.10 installed and have a great setup. However, I'm trying to install another OS on the hard drive and need to remove a partition. I've read online that I can remove the Swap partition and use a "Swap file". My question is this:

Is it possible to replace the Swap partition with a "swap file" without having to re-install linux? And if so, how do I accomplish this? 
........
You can also just resize your existing partitions using an Ubuntu install CD (search for detailed instructions).

After reading up on this, the main issue with a Swap file is the potential for it to be created in a non-contiguous manner (not using a continuous portion of disk space) which may affect performance compared to a Swap partition which is usually created in one single block of disk space.

I had thought that a Swap file would be affected by/affect the filesystem it was associated with, but the Linux kernel bypasses all filesystem components and accesses the disk directly for Swap IO.

---

### Post by forcecore on 2010-11-03
from 10.04 to 10.10 i use swapspace software and it works great, it creates swap file when needed.

---

### Post by mishathegoat on 2010-11-03
> **MooPi said:**
> I'm currently using a swap file, created with instructions from this page [https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")
Nice horns :)

Likewise :) Heh heh
Thanks for the quick response, the FAQ was just what I needed.

[QUOTE=dcstar]
You can also just resize your existing partitions using an Ubuntu install CD (search for detailed instructions).

After reading up on this, the main issue with a Swap file is the potential for it to be created in a non-contiguous manner (not using a continuous portion of disk space) which may affect performance compared to a Swap partition which is usually created in one single block of disk space.

I had thought that a Swap file would be affected by/affect the filesystem it was associated with, but the Linux kernel bypasses all filesystem components and accesses the disk directly for Swap IO. 
[/QUOTE]

Thanks for the useful info!

[QUOTE=forcecore]
from 10.04 to 10.10 i use swapspace software and it works great, it creates swap file when needed. 
[/QUOTE]

Thanks, do you happen to remember the name of the software?

---

### Post by forcecore on 2010-11-05
swapspace is name search from synaptic

---


---
title: "weird and stupid kernel update problem"
date: 2010-03-04
forum: General Help
---

### Post by chaopoch on 2010-03-04
This stupid problem ONLY happens in 9.10 and never be solved.

Today, there is another kernel update, as usual, it just updates linux-image-generic and linux-generic, but ignores the linux-headers-2.6.31-20, linux-headers-2.6.31-20-generic and linux-image-2.6.31-20-generic, if I do not installed the rest three packages, the system will not be able to enter the desktop after reboot.

According to the descriptions in Synaptic, the missed three packages are essential for linux-image-generic and linux-generic, why does the update manager always ignore them in 9.10?


[COLOR="Red"]**linux-generic**
This package will always depend on the **latest** complete generic Linux kernel
available.[/COLOR]

[COLOR="red"]**linux-image-generic**
This package will always depend on the **latest** generic kernel image
available.[/COLOR]

---


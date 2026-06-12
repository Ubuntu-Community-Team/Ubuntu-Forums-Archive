---
title: "Customized kernel and nVidia binary drivers?"
date: 2011-10-13
forum: General Help
---

### Post by chngr on 2011-10-13
Hi everybody,

I am building custom kernels using "make-kpkg" command - the debian way, everything works great even my nVidia propriatery driver. And this nvidia module confuses me so much.

When I build my kernel with standard "make", and install it as it is expected there is no nvidia module in my /usr/lib/kernel-ver directory and not surprisingly just copying this driver from older kernel to a new one doesn't work as well.

I wonder how can this nVidia binary driver still work if I compile my kernel with "make-kpkg"?
What this utility does to make it happen?

---


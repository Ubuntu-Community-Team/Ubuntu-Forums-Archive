---
title: "How to tell what real kernel version this is"
date: 2011-06-27
forum: General Help
---

### Post by Skaperen on 2011-06-27
How can I tell what the real kernel version is for a given Ubuntu kernel package which has Ubuntu's own sub-numbering system, and removes the 4th number of Linux kernel versions?  They seem to be rather effective at changing the kernel files around.

---

### Post by Joris Donders on 2011-06-27
The quick way is : press Ctrl +Alt +T an d type in the terminal ' uname -r' (without the '') 
then you know your kernel-version

---

### Post by Dave_L on 2011-06-27
This may be what you're looking for:
[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html)

There's more information here:
[https://wiki.ubuntu.com/Kernel/FAQ](https://wiki.ubuntu.com/Kernel/FAQ)

---

### Post by Skaperen on 2011-06-28
> **Joris Donders said:**
> The quick way is : press Ctrl +Alt +T an d type in the terminal ' uname -r' (without the '') 
then you know your kernel-version
That just gives me the same Ubuntu renumbered kernel.  What I want is the original kernel number it is based on.

> **Dave_L said:**
> This may be what you're looking for:
[http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html]("http://kernel.ubuntu.com/%7Ekernel-ppa/info/kernel-version-map.html")

There's more information here:
[https://wiki.ubuntu.com/Kernel/FAQ](https://wiki.ubuntu.com/Kernel/FAQ)

This at least works for kernels up to this date ... and further by refetching the table.  It would be nice if they left the actual number somewhere, like in the headers or some added file.  But this will do.

---


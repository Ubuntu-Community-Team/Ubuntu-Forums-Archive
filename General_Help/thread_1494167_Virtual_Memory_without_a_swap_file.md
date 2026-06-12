---
title: "Virtual Memory without a swap file?"
date: 2010-05-26
forum: General Help
---

### Post by stealth86 on 2010-05-26
Hi

I have a machine with 1 GB of RAM. I installed Ubuntu 10.04 without any swap partition.

I've noticed however that if I start Firefox, and view its memory usage with `top`, it reports that Firefox is using approximately 100 MB of resident memory, and 350 MB of virtual memory. 

How is this possible if no swap file/partition exists? Where is the kernel keeping this virtual memory?

thanks

---

### Post by Zemblan on 2010-05-26
[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

> The difference among VIRT, RES, and SHR in top output

VIRT stands for the virtual size of a process, which is the sum of memory it is actually using, memory it has mapped into itself (for instance the video card's RAM for the X server), files on disk that have been mapped into it (most notably shared libraries), and memory shared with other processes. VIRT represents how much memory the program is able to access at the present moment. RES stands for the resident size, which is an accurate representation of how much actual physical memory a process is consuming. (This also corresponds directly to the %MEM column.) This will virtually always be less than the VIRT size, since most programs depend on the C library.

SHR indicates how much of the VIRT size is actually sharable memory or libraries). In the case of libraries, it does not necessarily mean that the entire library is resident. For example, if a program only uses a few functions in a library, the whole library is mapped and will be counted in VIRT and SHR, but only the parts of the library file containing the functions being used will actually be loaded in and be counted under RES.

Virtual memory is not the same as swap. At the top of the  'top' output you'll see something like this:

[IMG]http://dl.dropbox.com/u/5066517/Screenshot.png[/IMG]

Note the swap line below the memory line. Presumably if you have no swap space you wont be seeing that line.

---

### Post by stealth86 on 2010-05-26
That makes sense. Thanks for the link.

---


---
title: "RAM Partitioning"
date: 2011-06-05
forum: General Help
---

### Post by Tao Xuin on 2011-06-05
Hi guys, I was wondering if there is a good (easy to use) program that would allow me to partition parts of my RAM specifically for games. A friend of mine uses Ramdisk on Windows and I was hoping for something similar. Could anyone point me to a good program and tutorial for this?

I'm using 10.4 btw.

---

### Post by wolfen69 on 2011-06-05
There is no need for this, as the system will automatically allocate what it needs for whatever you are running. And linux is also very efficient at dealing with memory.

---

### Post by dFlyer on 2011-06-05
> **Tao Xuin said:**
> Hi guys, I was wondering if there is a good (easy to use) program that would allow me to partition parts of my RAM specifically for games. A friend of mine uses Ramdisk on Windows and I was hoping for something similar. Could anyone point me to a good program and tutorial for this?

I'm using 10.4 btw.

Let linux manage your memory.

---

### Post by Mark Phelps on 2011-06-06
Your question and comments are contradictory ...

A RamDisk is the allocation of memory to simulate a file system.  It allows you to treat memory as if it were disk space.  That permits running stuff a lot faster because once loaded, it generally does not have to access the hard drive very often.

System memory allocation, on the other hand, is dynamic -- and you have no way to really control how much memory it allocations to processes.

---


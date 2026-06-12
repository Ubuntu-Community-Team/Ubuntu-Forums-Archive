---
title: "Help bisecting a kernel"
date: 2011-09-23
forum: General Help
---

### Post by jdgregson on 2011-09-23
Hello, 
    I posted a bug report for a GPU hang with my video card driver. Now the developers looking into the problem would like me to bisect the kernel. Problem is, I don't really know how. They sent a link to this page, [https://wiki.ubuntu.com/Kernel/KernelBisection](https://wiki.ubuntu.com/Kernel/KernelBisection), which did help, but I still don't know enough to start the bisection. 

    The first problem I am running into is, on the line after 
**Take a look first to see what you can learn**

I don't know what the kernels I need to bisect are tagged, and can't figure it out. 

Here is the but report, if it helps. [https://bugs.freedesktop.org/show_bug.cgi?id=41099](https://bugs.freedesktop.org/show_bug.cgi?id=41099)

Please help me through this. I would like to help solve this problem, but as the developers said, they don't have time to walk me through it, or to bisect the kernels themselves. Is there somebody else who is able and willing to build the kernels, and have me test them?

---

### Post by Blasphemist on 2011-09-23
I haven't done this either but I'll try to help. It looks to me like the bad kernel tag is clear, Ubuntu 3.0.0-11.18, but I didn't see from the bug report if this has always happened since you upgraded to oneiric. I don't think kernel bisection is going to work if you have to go back very far in kernels. There would be so many commits between the versions. I know the 3.0.0-9.15 was a beta 1 kernel. Do you have still have your older kernels installed? You could see them on the grub boot screen and in synaptic.

---


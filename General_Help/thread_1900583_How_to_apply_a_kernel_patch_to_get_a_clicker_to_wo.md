---
title: "How to apply a kernel patch to get a clicker to work"
date: 2011-12-26
forum: General Help
---

### Post by eggmanneo on 2011-12-26
Hi, I got an August LP107T presentation clicker that's not working in Ubuntu 11.10.  I was searching online and I found this post [https://lkml.org/lkml/2011/1/20/429]("https://lkml.org/lkml/2011/1/20/429")  which seems to suggest that this clicker shares the same USB id as another device.  This post also posted a patch to the linux kernel that might fix this problem.  However, (1) I don't know how to apply patches to linux kernels and (2) I couldn't tell exactly which chunk of this post contained the code for the kernel patch.  My kernel version is 3.0.0-14-generic
Any help with applying the patch or with an alternative solution would be appreciated.

---

### Post by Bobhuber on 2011-12-26
> **eggmanneo said:**
> Hi, I got an August LP107T presentation clicker that's not working in Ubuntu 11.10.  I was searching online and I found this post [https://lkml.org/lkml/2011/1/20/429](https://lkml.org/lkml/2011/1/20/429)  which seems to suggest that this clicker shares the same USB id as another device.  This post also posted a patch to the linux kernel that might fix this problem.  However, (1) I don't know how to apply patches to linux kernels and (2) I couldn't tell exactly which chunk of this post contained the code for the kernel patch.  My kernel version is 3.0.0-14-generic
Any help with applying the patch or with an alternative solution would be appreciated.
Applying a kernel patch means compiling your own Kernel which is for advanced users and not something you would do or even attempt unless you knew what you were doing . Normally a Kernel Patch is  posted by the developer with instructions on how to apply it for testing and then submitted as part of the  Kernel release. The patch you referenced looks like it's old (comparatively speaking in terms of kernel releases and testing), not tested at the time it was posted , and may well have been implemented in some of the newer Kernel releases or in fact discarded if it didn't work. To give you an idea of the current releases and testing for ubuntu > [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Kernel source archives are found here > [http://www.kernel.org/](http://www.kernel.org/)
I do compile my own Kernel (lean and mean) but also keep about four sets of backups  LOL. As for your problem and looking at the post I see no easy solution.

---


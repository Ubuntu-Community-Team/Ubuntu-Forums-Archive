---
title: "Differences in Kernels"
date: 2006-06-08
forum: General Help
---

### Post by Archangel_X19 on 2006-06-08
I only bring this up because I recently switched back from archlinux to ubuntu and in one of their forums it talked about how since they package i686 architecture packages that it makes the most sense to have a kernel that is built i686.  This got me thinking, I tend to play around more on ubuntu because the community support is so phenomenal that I started compiling my own kernels and putting ubuntu on others computers and so on.  But does the fact that I compile my kernel for a pentium 4 and make it SMP hurt the speed of my system because the packages are i386?  I know there was a similar discussion on this but I think my approach is different.  I just want to know if making a custom kernel with a mismatch in architecture hurts, improves, or leaves my system the same.  Any feed back would be awesome.  If its positive I recompile a kernel tonight.  If its not, I get fglrx drivers working on my current kernel.

---

### Post by DarthMandeep on 2006-06-08
I'm no expert on C compiler optimizations, but I really can't imagine that running a 686 optimized kernel with 486 optimized software would result in a performance penalty.

---

### Post by 23meg on 2006-06-08
> But does the fact that I compile my kernel for a pentium 4 and make it SMP hurt the speed of my system because the packages are i386?If that were the case any distro that shipped 686 kernels yet not all packages optimized for 686  (namely Ubuntu?) would be at an elementary fault. And they aren't; neither are you.

For what I know the kernel and a few core libs are where the optimization actually pays off, and where it does pay off it's already done in Ubuntu.

---

### Post by Archangel_X19 on 2006-06-09
I just wanted to make sure before I went all crazy tweaking my kernel and fglrx'ing it all to death.  I had great success with the 2.6.16 kernel and fglrx so I wanted to go back to it with dapper.  Thanks for the responses guys I appreciate the feedback on the matter.  Now its time to tweak.

---


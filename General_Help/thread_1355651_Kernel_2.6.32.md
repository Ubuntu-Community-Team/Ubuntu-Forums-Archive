---
title: "Kernel 2.6.32"
date: 2009-12-15
forum: General Help
---

### Post by risingsun on 2009-12-15
Hi, I was just thinking about trying out kernel 2.6.32. I have two options, compiling it or using the deb packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

However I have a few questions about each approach:

a) With compiling do I apply a single latest patch or multiple progressive patches? E.g. kernel.org has a git patch at [http://www.kernel.org/pub/linux/kernel//v2.6/snapshots/patch-2.6.32-git11.bz2](http://www.kernel.org/pub/linux/kernel//v2.6/snapshots/patch-2.6.32-git11.bz2) but I am unsure whether I only apply this patch and whether it's applied to version 2.6.31 or 2.6.32 since I've read that you apply it to the prior version since there is no full release for 2.6.32 yet. 

Alternatively, there is a stable release of 2.6.32.1 listed on kernel/org with the full source code, would this already include all stable patches up to that point?

b) I could also use the test debian package from the ubuntu kernel test thing. If so, which would I use? I see both a 2.6.32 release candidate 8 and a plain 2.6.32. 2.6.32 plain has the later modified time so I might presume that this is the most up to date and thus the one to use, or is it most current test version and rc8 is the current most stable test version?

Many thanks.

---

### Post by audiomick on 2009-12-15
> **risingsun said:**
>  If so, which would I use? I see both a 2.6.32 release candidate 8 and a plain 2.6.32. 2.6.32 plain has the later modified time so I might presume that this is the most up to date and thus the one to use

I would think so too.

---

### Post by ean5533 on 2009-12-15
> **risingsun said:**
> a) With compiling do I apply a single latest patch or multiple progressive patches? E.g. kernel.org has a git patch at [http://www.kernel.org/pub/linux/kernel//v2.6/snapshots/patch-2.6.32-git11.bz2](http://www.kernel.org/pub/linux/kernel//v2.6/snapshots/patch-2.6.32-git11.bz2) but I am unsure whether I only apply this patch and whether it's applied to version 2.6.31 or 2.6.32 since I've read that you apply it to the prior version since there is no full release for 2.6.32 yet.

Alternatively, there is a stable release of 2.6.32.1 listed on kernel/org with the full source code, would this already include all stable patches up to that point?
You shouldn't need to apply any patches. Patches are only used when you want to apply changes that don't already exist in a stable release; for example, release candidates, which are a step between "beta" and "stable". From the example listed on the kernel.org FAQ (which I think you read), to get kernel version 2.6.14-rc5, you would apply the 2.6.14-rc5 patch to the stable release of 2.6.13. However, you would only need to do that if the there weren't already a stable version of 2.6.14 out, which there is. 

Similarly, kernal version 2.6.32 already exists as a stable version. You can download the full source code of that version and compile it without needing to apply any patches.


> **risingsun said:**
> b) I could also use the test debian package from the ubuntu kernel test thing. If so, which would I use? I see both a 2.6.32 release candidate 8 and a plain 2.6.32. 2.6.32 plain has the later modified time so I might presume that this is the most up to date and thus the one to use, or is it most current test version and rc8 is the current most stable test version?

Many thanks.
A release candidate is a version **before** the stable release, not after. In other words, 2.6.14 is "better" than 2.6.14-rcXXX. So, the 2.6.32 version is what you're looking for, not the release candidate.

As a final note, may I ask why you're compiling a kernel at all? If it's just for performance reasons, there are a couple things to consider:

[LIST=1]
[*]If you're using a 64-bit version of Ubuntu, you really don't need to compile a kernel from source to get good optimizations. 64-bit versions are already VERY optimized for newer processors (because there aren't any old 64-bit processors to worry about!).
[*]If you're using a 32-bit version then it may be worth compiling the kernel from source to get some performance benefits, but don't expect anything amazing. Numbers I've read said performance on a Core i7 processor was only increased 5-10% for a compiled-from-source kernel compared to a "stock" kernel. Also, people on support forums will be very likely to point at your compiled-from-source kernel as the root cause of every problem you encounter, and it could make it harder to get support for any problems you encounter. Bug reports, for example, will be invalid if you're not using a kernel version distributed by Ubuntu.[/LIST]

I'm not trying to scare you off or anything, just wanted to make it clear that compiling from source isn't a magical performance boost with no downsides.

---

### Post by risingsun on 2009-12-16
Ah, wonderful, thank you for the replies. :)

As for the reason, it's mostly to see what the performance of the new scheduler in 2.6.32 is like as well as a bit of practice in compiling a kernel, though it's perfectly possible it won't be an improvement :) 

I'm aware that it'll invalidate bug reports and the like though since it's in effect a custom build, which is why I'll be leaving the old kernels on the system in case I need to roll back.

---

### Post by ean5533 on 2009-12-16
> **risingsun said:**
> I'm aware that it'll invalidate bug reports and the like though since it's in effect a custom build, which is why I'll be leaving the old kernels on the system in case I need to roll back.
I love the smart ones. :)

---


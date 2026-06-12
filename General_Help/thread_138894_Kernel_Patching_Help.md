---
title: "Kernel Patching Help"
date: 2006-03-02
forum: General Help
---

### Post by henry95 on 2006-03-02
I am running kernel 2.6.12 and trying to patch it with this patch:
kft-all-in-one-2.6.12.patch

i was wondering how i go about doing this?

I have read this: [https://wiki.ubuntu.com/KernelHowto?highlight=%28kernel%29%7C%28recompile%29]("https://wiki.ubuntu.com/KernelHowto?highlight=%28kernel%29%7C%28recompile%29")


but i don't know when to apply the patch.  Am I going about this the wrong way?

-henry

---

### Post by mlind on 2006-03-02
You should apply patches after you have extracted your kernel source, and before
configuring it. I will still manually do *make mrproper* before applying
pacthes, which will ensure that kernel tree is clean. Make -commands need to
be executed on root of the tree.

Then apply your patches and proceed to configuring the kernel. You should clone
existing Ubuntu kernel by doing *make oldconfig*, it's explained well on that
wiki document.

If you need to change kernel's configuration, use either *make xconfig* or [I]make
gconfig[/I] which will allow you to edit parameters with visual editor.

Then you follow the rest of the steps.

---

### Post by moberry on 2006-03-02
Make sure back your .config up. mrproper deletes the custom config.

---

### Post by jeremiebergeron on 2006-03-03
Just as a note, if you're running a stock ubuntu kernel you cannot patch it without getting the sources and compiling. So unless you really need to patch the kernel with a critical patch or you feel like compiling the kernel for fun, it's not usually worth it since the stock ubuntu kernel (at least the 686 kernel) is quite adequate.

---


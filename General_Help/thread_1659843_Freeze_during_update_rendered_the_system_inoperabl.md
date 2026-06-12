---
title: "Freeze during update rendered the system inoperable"
date: 2011-01-04
forum: General Help
---

### Post by Louigi Verona on 2011-01-04
What happened was a random freeze, which unfortunately occurs on my Ubuntu 10.04, during the update. At that time the downloaded software was installing, namely the linux kernel (hehehe).

I rebooted, the system performed a disc check and then loaded stripes. Instead of the cursor - a large striped square. It must be noted that during disc check Ubuntu logo was not displayed but normal text instead, saying "Ubuntu 10.04".

Tried recovery mode - however, it stops loading during bottom init scripts, on saying that it allocates swap or something like that.

What should I do to fix the system?

---

### Post by hawthornso23 on 2011-01-04
During bootup, spam the shift or esc keys (depends on your version of grub) to get into the grub menu. From there you should be able to boot into the old kernel. 

Also suggest you run memtest (from grub menu) and leave it running overnight. Random freezes can be caused by bad memory. Installing a new kernel with bad memory may have caused your problem.

Edit: The symptoms you describe could be a video driver problem. Kernel updates do often muck up proprietary video drivers. If you can get the system running try disabling/uninstalling/reinstalling proprietary video drivers (if you have any) and see if that enables you to boot into the new kernel.

---

### Post by Louigi Verona on 2011-01-05
How can I switch off the drivers if when I log on to the system I cannot do anything?

---


---
title: "Lucid, kexec, and custom kernels."
date: 2010-11-13
forum: General Help
---

### Post by jwbrase on 2010-11-13
I'd been using Jaunty up till a month or two ago on my laptop, and upon upgrading to Lucid noticed that rebooting (at least through the GUI, I'm not sure I've tried it with shutdown -r yet) now just kexecs a new kernel in rather than actually doing a full hardware reboot. A few days ago I compiled myself a custom kernel, and I've noticed that when I reboot from the custom kernel, it kexecs into the latest offical kernel (2.6.32.26), rather than into the custom kernel. I assume that there must be some seting somewhere telling it which kernel to boot, but I can't seem to figure out where, and my Google-fu hasn't been able to sniff it out either. Searching for stuff like "lucid reboot" tends to throw out a bunch of stuff for general reboot problems with lucid, and searching for "lucid kexec" seems to turn up more general information on kexec than the fact that lucid uses it for reboots. Can anybody give me any pointers?

---


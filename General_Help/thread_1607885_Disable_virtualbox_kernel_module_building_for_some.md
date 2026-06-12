---
title: "Disable virtualbox kernel module building for some kernels"
date: 2010-10-28
forum: General Help
---

### Post by k999 on 2010-10-28
I'm running Ubuntu 10.04.1, and I've built and installed my own vanilla Linux 2.6.36 kernel from Linus Torvalds' 2.6 tree, copying Ubuntu's .config and running "make oldconfig" and mostly going with defaults. 

I have installed virtualbox, and it tried to build the modules for the 2.6.36 kernel, but they failed for my self-compiled kernel, and worked for the Ubuntu kernel. Now that package is marked as failed during installation, so every time I install or update something, the module build runs again, and fails - again.

Is there a way to stop the package from trying to build the modules for some kernels, and mark the package as successfully installed? I just want it to stop building those modules all the time.

---


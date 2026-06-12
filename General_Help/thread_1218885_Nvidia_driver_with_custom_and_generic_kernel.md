---
title: "Nvidia driver with custom and generic kernel"
date: 2009-07-21
forum: General Help
---

### Post by Pyntux on 2009-07-21
Hello!

Can I have nvidia driver with custom kernel and generic kernel to? Something like in Arch Linux where in abs I make packet of nvidia driver and rename it to name of custom kernel, so that modul use my custom kernel, but generic kernel can use nvidia driver from repo...can I do something like that on Ubuntu? Or how?

---

### Post by Pyntux on 2009-07-28
Anybody? Please?

---

### Post by steveneddy on 2009-08-02
I actually have the exact same question.

I have rolled a couple of custom kernels and would like to have the nvidia driver in the repos, I'm using the nvidia-glx-new-envy video driver.

I am also using VirtualBox and would like to have a kernel module for the new kernels as well.

I'm no expert but I can follow detailed instruction effectively.

Any help appreciated.

Cheers - :popcorn:

---

### Post by ridetheteapot on 2009-08-02
run nvidia installer with -K flag to build the kernel modules per kernel for the different kernels.
for the repo driver, i would have guessed they would hook you up without even asking.

edit ---
i should add you can buld for the module for non running kernel with the -k <kernel-name> flag
as well as the --kernel-source-path=<path> for custom headers if you need it.

all info is available with -A flag on installer

---

### Post by steveneddy on 2009-08-05
> **ridetheteapot said:**
> run nvidia installer with -K flag to build the kernel modules per kernel for the different kernels.
for the repo driver, i would have guessed they would hook you up without even asking.

edit ---
i should add you can buld for the module for non running kernel with the -k <kernel-name> flag
as well as the --kernel-source-path=<path> for custom headers if you need it.

all info is available with -A flag on installer

Great info - thanks

---


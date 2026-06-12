---
title: "Do I have to recompile the kernel to enable CONFIG_MODULE_FORCE_UNLOAD?"
date: 2012-03-05
forum: General Help
---

### Post by ryanstd on 2012-03-05
'm trying out how to write kernel modules and accidentally made the toy module unloadble: Device or resource busy. I searched that by enabling CONFIG_MODULE_FORCE_UNLOAD, we can force unloading the module. The option can be seen in /usr/src/xxx/.config. After changing the entry there? Do I need to cd to the dir and recompile it? Thanks!

---

### Post by pbrane on 2012-03-05
yes you do. Those are build configuration options in the .config file. Have a look at these links. The first one is for building an upstream kernel. The second is for building an ubuntu kernel
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")
[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

---


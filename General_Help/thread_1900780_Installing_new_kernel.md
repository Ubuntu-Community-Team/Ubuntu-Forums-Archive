---
title: "Installing new kernel"
date: 2011-12-27
forum: General Help
---

### Post by theone419 on 2011-12-27
ok so im following this guide```
 http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization
```my RT kernel is 3.2.0-rc1-rt1
my patch is 3.2-rc1-52e4c2a05-rt1.patch

I have successfully compiled my new kernel image and headers that are sitting in /usr/src

Right now I am stuck on the Prep for boot section, I cannot find my bootloader and I don't even know what I am using. Fresh install of ubuntu 11.04 natty x64 . I already tried to reboot and uname -r outputs the stock kernel, so whats going on here? Help would be appreciated.

---

### Post by Bobhuber on 2011-12-27
> **theone419 said:**
> ok so im following this guide```
 http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization
```my RT kernel is 3.2.0-rc1-rt1
my patch is 3.2-rc1-52e4c2a05-rt1.patch

I have successfully compiled my new kernel image and headers that are sitting in /usr/src

Right now I am stuck on the Prep for boot section, I cannot find my bootloader and I don't even know what I am using. Fresh install of ubuntu 11.04 natty x64 . I already tried to reboot and uname -r outputs the stock kernel, so whats going on here? Help would be appreciated.
First of all no way would I apply that patch to a a system I depended on.
Second on ubunu with  DKMS installed you don't need to prep for boot. 
Read these.
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Its easiest to use the instructions (Compile the old fashioned Debian way) and get help from the Git page to explain some things.
If you want to compile a kernel that matches your system wihtout all the additional drivers just use 
make localmodconfig when building the .config file and  add the additional drivers you will need using make menuconfig before you compile the modules.After you have created image and header .deb files just use dpkg -i  <name of files> to install them and reboot. Note if you are using proprietary video drivers (ATI or NVIDIA) you will have to  reinstall  them before you will be able to boot into the new kernel.

---

### Post by theone419 on 2011-12-28
> **Bobhuber said:**
> First of all no way would I apply that patch to a a system I depended on.
Second on ubunu with  DKMS installed you don't need to prep for boot. 
Read these.
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Its easiest to use the instructions (Compile the old fashioned Debian way) and get help from the Git page to explain some things.
If you want to compile a kernel that matches your system wihtout all the additional drivers just use 
make localmodconfig when building the .config file and  add the additional drivers you will need using make menuconfig before you compile the modules.After you have created image and header .deb files just use dpkg -i  <name of files> to install them and reboot. Note if you are using proprietary video drivers (ATI or NVIDIA) you will have to  reinstall  them before you will be able to boot into the new kernel.

sorry for the late reply, I ended up switching providers, the custom kernel didn't work out, but now I know how to do it, if anything ill come back for assistance.

---


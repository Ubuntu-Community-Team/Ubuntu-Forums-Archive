---
title: "Please help me understand what this joker is talking about"
date: 2011-07-03
forum: General Help
---

### Post by ClientAlive on 2011-07-03
I'm reading this web page about compiling the Linux kernel and something the guy says in there doesn't make sense to me. Can someone please help me understand?

It sounds like he's making a difference between the kernel "source code" and the kernel itself (as in the downloaded file/ files) but the way he talks about both is the same. I'm confused!

> 
It is advisable to _install_ the kernel source code that comes with your distribution, because the various GUIs are then automatically installed too. Once this is done the tarball with the newest Linux kernel, e.g.,the file 'linux-2.4.6.tar.bz2' can be downloaded . . .

Reference: [http://linuxfocus.org/English/July2002/article252.shtml](http://linuxfocus.org/English/July2002/article252.shtml)


Underline is mine:

So then, if one had already "installed" the "kernel sources code," why would he need the "tarball with the newest Linux kernel?" He's already "installed" a kernel, right?

:confused:

---

### Post by jocko on 2011-07-03
Irrespective if you understand what he meant, that page is nine years old. I'm sure you can find more current instructions.

But I think he meant *exactly* what he wrote; If you install the kernel source package that comes with your distro, you will then also automatically install the tools you need in order to compile the kernel. Note that installing your distro's kernel source package simply downloads the source tarball from the distro's repositories and unpacks it in /usr/src, it does NOT compile and install the kernel. He did this *only* to get the tools, he was not interested in the distro's kernel, since there was a newer one available at kernel.org.
Then he continues talking about replacing the distro's source package with the newer one from kernel.org, and then how to compile and install it.

---

### Post by prodigy_ on 2011-07-03
If you want some up-to-date info about compiling Linux kernel, I'd recommend:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[http://www.gentoo.org/doc/en/articles/linux-kernel-compiling.xml](http://www.gentoo.org/doc/en/articles/linux-kernel-compiling.xml)

---

### Post by ClientAlive on 2011-07-03
> **jocko said:**
> Irrespective if you understand what he meant, that page is nine years old. I'm sure you can find more current instructions.

But I think he meant *exactly* what he wrote; If you install the kernel source package that comes with your distro, you will then also automatically install the tools you need in order to compile the kernel. Note that installing your distro's kernel source package simply downloads the source tarball from the distro's repositories and unpacks it in /usr/src, it does NOT compile and install the kernel. He did this *only* to get the tools, he was not interested in the distro's kernel, since there was a newer one available at kernel.org.
Then he continues talking about replacing the distro's source package with the newer one from kernel.org, and then how to compile and install it.


> **prodigy_ said:**
> If you want some up-to-date info about compiling Linux kernel, I'd recommend:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[http://www.gentoo.org/doc/en/articles/linux-kernel-compiling.xml](http://www.gentoo.org/doc/en/articles/linux-kernel-compiling.xml)

 Awesome! Got ya'. Thanks fellas. Sure appreciate it.

---


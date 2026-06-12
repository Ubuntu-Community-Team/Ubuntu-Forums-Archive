---
title: "jaunty virtualbox driver setup fails"
date: 2009-12-25
forum: General Help
---

### Post by Newbie123 on 2009-12-25
Hi everyone.

Here is the problem.

1. Running Jaunty, due to video card problems, I had to manually upgrade my kernel to 2.6.30-02063010-generic. I installed from the ubuntu ppa: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.10/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.10/)
I've installed the linux-headers-all, linux-image-386, linux-source-all. I can boot into the new kernel, it fixes the old video card problem, and everything else works except for virtualbox.

2. I installed virtualbox 3.1.2. The problem is it can't compile the the vboxdrv. When I run /etc/init.d/vboxdrv setup, I get the following error:

** Compiling vboxdrv
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/3.1.2/source ->
                 /usr/src/vboxdrv-3.1.2

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.30-02063010-generic cannot be found at
/lib/modules/2.6.30-02063010-generic/build or /lib/modules/2.6.30-02063010-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.



Maybe I need to specify a directory for the --kernelsourcedir option. Does anyone have any ideas? Is there anyway I can manually compile the modules?

Thanks

---

### Post by Newbie123 on 2009-12-25
I figured out what was wrong by trial and error.

For whatever reason, installing linux-headers-all doesn't trigger dkms to recompile the virtualbox drivers.

I installed the following 386 version:


linux-headers-2.6.30-02063010-generic_2.6.30-02063010_i386.deb

Then I ran /etc/init.d/vboxdrv setup and now it works.

I hope this is useful to someone else.

---


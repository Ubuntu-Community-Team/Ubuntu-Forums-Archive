---
title: "Ubuntu unable to see sata drives"
date: 2006-06-19
forum: General Help
---

### Post by nameiwantistaken on 2006-06-19
I'm using an Asus motherboard that is using the VIA VT8251 chipset.  This leads to sata drives straight up not working.  This chipset is not supported in the current version of the kernel that 6.06 uses 2.6.15.23.  Apparently, it did work in earlier 6.06 versions using kernels that were from 2.6.15.15=19, but it no longer works.

The only workaround that I have found is to upgrade the kernal to 2.6.16 to get a driver that works and then move the image of this over to the SATA drive.  This plan isn't working out so well.

I tried following the guide that someone wrote on here, but it still has no changed anything with the kernel.  It is still at 2.6.15.   My questions now really are:

Is there an easy graphical way to move up the kernel

Once I have the kernel copied, how can I move this over to my SATA drive

Are there any other ways that I can handle this?  I'm open to suggestions.

---

### Post by nameiwantistaken on 2006-06-19
Anyone?

---

### Post by nameiwantistaken on 2006-06-19
Bump

---

### Post by jamuir on 2006-06-20
I posted some info about the vt8251 in another [thread]("http://www.ubuntuforums.org/showthread.php?t=196171").  I suggest you follow the links there and read some of the posts in the VIA forum.

Compiling a new kernel is not that difficult.  I followed directions that I think were listed at 
[https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto).  However, that wiki page seems to have been recently deleted.  There were about 3 wiki pages with similar instructions.  I wonder if someone decided to clean house.

I recommend you use debian's kernel package to make .deb files containing your new kernel image.  Look for instructions that use "make-kpkg".  Then you can install the new image using dpkg -i new_kernel_image.deb

Sorry I can't give you explicit instructions.  Keep trying and you'll get it.

-James

---

### Post by dcstar on 2006-06-21
I have found this thread very useful for compiling a kernel:

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

I have been using my own kernel version with the Via UniChrome drivers compiled into the kernel (rather than loading as a module), the ability to directly choose support for your particular hardware can make things run a bit smoother.

---

### Post by nameiwantistaken on 2006-06-24
I updated the kernel following instructions I found on one of the links and it wouldn't go to desktop.  I tried commenting out the loading of drivers and downloading video drivers, but they were for non-debian distros and I ended up going with different hardware.  In my opinion, Ubuntu should be using the latest kernel.  It is meant to be a desktop alternative, yet without the use of the newer kernels it lacks the device driver support necessary.  This was a little much to expect of a first time user to deal with.

---


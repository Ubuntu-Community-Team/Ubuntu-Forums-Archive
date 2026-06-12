---
title: "Two different linux-header packages?"
date: 2006-01-31
forum: General Help
---

### Post by dolson on 2006-01-31
What is the difference between these two files?

linux-headers-2.6.12-10_2.6.12-10.26_i386.deb
linux-headers-2.6.12-10-386_2.6.12-10.26_i386.deb

I followed the tutorial here: [https://wiki.ubuntu.com/KernelBuildpackageHowto](https://wiki.ubuntu.com/KernelBuildpackageHowto)

Just trying to figure out why there are two separate header packages...

Thanks in advance.

---

### Post by az on 2006-01-31
Whether you make the linux-headers package for 386, 686, k7 or any other arch, there will be some files in common.  linux-headers-2.6.12-10_2.6.12-10.26_i386.deb contains the files that are common to all arches.  Otherwise, you would not be ablt to install more than one specific linux-headers package at a time.

linux-headers-2.6.12-10-386_2.6.12-10.26_i386.deb just contains what is specific to 386 and it deopends on linux-headers-2.6.12-10

---

### Post by dolson on 2006-01-31
Thanks!

So I would install both then, along with my kernel image package.

---


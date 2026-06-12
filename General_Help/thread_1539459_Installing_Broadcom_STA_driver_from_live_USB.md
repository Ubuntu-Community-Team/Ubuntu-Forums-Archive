---
title: "Installing Broadcom STA driver from live USB"
date: 2010-07-26
forum: General Help
---

### Post by TriBlox6432 on 2010-07-26
Okay, I have a Dell Mini 10v and no wireless.  Ubuntu desktop is  installed.  I do not have any access to a wired connection.  I inserted  the live USB while I was already booted from my hard disk and went to  pool>restricted>b>bcmwl.  When I double click on the  bcmwl-kernal-source_5.60.48.36+bdcom-0ubuntu3_i386.deb Package Installed  pops up, but I get an error message saying "Error: Dependency is not  satisfiable: dkms"

What should I do to get my wireless working?

---

### Post by TriBlox6432 on 2010-07-26
Bump?

---

### Post by Tylerjd on 2010-07-26
> **Dynamic Kernel Module Support (DKMS)** is a framework used to generate [Linux]("http://en.wikipedia.org/wiki/Linux") [kernel modules]("http://en.wikipedia.org/wiki/Loadable_kernel_module") whose sources do not generally reside in the [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") [source tree]("http://en.wikipedia.org/wiki/Source_tree").  ([http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)) 

Meaning that you don't need to compile a lot of kernel modules manually. (Easy Explanation)

Now on to your problem:
Do you have access to another computer, and a flash drive? If so you can download the DKMS package on to the flash drive, install, and try again. ([http://packages.ubuntu.com/lucid/admin/dkms](http://packages.ubuntu.com/lucid/admin/dkms))

---


---
title: "Manual kernel compile advantages"
date: 2011-07-12
forum: General Help
---

### Post by Anton K on 2011-07-12
Hi everyone!

Could anyone suggest is it possible to get advantages from manual kernel compilation for x86 platform?

As I understand, binary kernel from repositories are compiled with the most generic options, which provides the highest compatibility?

P.S. I'm sure this question isn't new and is typical for Ubuntu newbies. However, I haven't found competent answers yet.

P.P.S. I understand problems which are caused by this non-Ubuntu way.

Thank you for attention.

---

### Post by nothingspecial on 2011-07-12
In a nutshell, unless you are trying to run ubuntu on a toaster or a fridge, the only advantage in compiling your own kernel would be that you'll learn how to compile your own kernel.

---

### Post by garvinrick4 on 2011-07-12
Here is index of kernels in .deb download the all.deb,headers.deb and kernel.deb and install
in that order. Use your own 32 or 64 bit of course. Can use the sudo dpkg -i (package) in CLI
or click on downloaded .deb package and will go through GUI. Just stating different ways for
the new comers to understand. So if you want to practice compiling go ahead as in previous
post stated but always easier in .deb 
#I use the 3.0 kernel in Natty because my network card driver works better in 3.0 "iwlagn" driver intel.

[Index of /~kernel-ppa/mainline]("http://webcache.googleusercontent.com/search?q=cache:m77I8WvzXBoJ:kernel.ubuntu.com/%7Ekernel-ppa/mainline/+latest+ubuntu+kernel+in+.deb&cd=1&hl=en&ct=clnk&gl=us&client=ubuntu&source=www.google.com")

---


---
title: "Building kernel driver Ubuntu 12.04"
date: 2012-06-21
forum: General Help
---

### Post by clirakis on 2012-06-21
Hi, 
I'm trying to compile a kernel driver on an Ubuntu system. I have previously used other linux distributions and decided to change to Ubuntu. 

I have gotten the kernel headers. Specifically I am using linux-headers-3.2.0-25. 
What I am unclear on is which asm directory to use. in /usr/src/linux-headers-3.2.0-25/include there is an asm-generic. In /usr/src/linux-headers-3.2.0-25/arch/x86/include there is an asm directory as well. Using one or the other both lead to problems in compilation. 

Is there a piece that I am missing?
Regards, 
Chris

---

### Post by shumi on 2012-06-21
You need the kernel image too.
I followed a tutorial and it lead me to this site where there are all kernels.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

and all you need to do is too download the generic version, the all version and the image version.
and after that i used the terminal to install them.

sudo dpkg -i linux*.deb

make sure to be in the correct folder and there are only those 3 files that start with linux

hopefully it helped you.

---

### Post by clirakis on 2012-06-23
So not exactly. I'm curious as to why I need the full source to compile a kernel module. I would think that the headers provided through apt along with the libraries would be sufficient. 

My main complaint is that the headers appear to be inconsistent. 

If I were to compile against a generic kernel, wouldn't that imply that I would have to load that kernel at boot?

Chris

---

### Post by clirakis on 2012-07-05
Still hoping someone has something useful for me. 
I've tried a number of things all of which don't work. 

There appear to be a number of broken symbolic links in the source headers and generic kernel distribution. I've been able to do this rather seamlessly on other linux distros. 

Should I just give up and go to kernel.org and install that? Seems like this defeats the whole idea of having packages!!

---


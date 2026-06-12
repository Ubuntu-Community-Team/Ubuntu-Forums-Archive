---
title: "no light with acer aspire 7715z[no new linux version works]"
date: 2011-07-13
forum: General Help
---

### Post by yodasnubben on 2011-07-13
Hello!

I have problem with the latest linux distors, there is no light on the screen

its a acer sprite 7715z, i had ubuntu 9.04/10.04 and opensuse(dont remeber what version it was) on it before and it worked fine


I tryed the latest versions of opensuse, debian, fedora & ubuntu and it no light on the screen after it booted the system


i searched on google a while and i found some bug reports about same problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/756579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/756579)


so what can i do? is it something with the kernel?  How can i fix this? 

I seriously **need** linux for my job.. (We are switching from windows to linux and i have to get used to it so i can keep my job)


Thanks in advance!!

---

### Post by Mark Phelps on 2011-07-13
There is no such thing as "switching to Linux" anymore than there is "switching to Windows".

Why?

Linux is basically an operating system kernel.

The Distributions (known as Distros), package that kernel (or, really, a specific version of that kernel) with a bunch of other stuff, including drivers and applications.  It's THAT what you install to a PC.

So, basically, what you need to find out is what Distro of Linux your company is planning to use. That's important because, if they expect you to know minor details (i.e., System Admin level), you really need to know them for the particular Distro they are going to use.

If you then can't get THAT distro installed on your PC, you have a serious problem.

---

### Post by yodasnubben on 2011-07-16
> **Mark Phelps said:**
> There is no such thing as "switching to Linux" anymore than there is "switching to Windows".

Why?

Linux is basically an operating system kernel.

The Distributions (known as Distros), package that kernel (or, really, a specific version of that kernel) with a bunch of other stuff, including drivers and applications.  It's THAT what you install to a PC.

So, basically, what you need to find out is what Distro of Linux your company is planning to use. That's important because, if they expect you to know minor details (i.e., System Admin level), you really need to know them for the particular Distro they are going to use.

If you then can't get THAT distro installed on your PC, you have a serious problem.



i figured out that the problem is coused by xorg
can i downgrade it or something? because it works wit a bit older distros

---


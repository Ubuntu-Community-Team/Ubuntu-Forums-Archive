---
title: "How to download Ubuntu kernel"
date: 2011-10-03
forum: General Help
---

### Post by ramosdelpalo9 on 2011-10-03
For what I understand, Ubuntu is the main Unix-like OS others are based on. In other words, that Kubuntu, Mint, Xubuntu, etc. are Ubuntu-like OS. Please tell me if I am right.

If so, I would like to know where I can download the Ubuntu kernel source code, but download it FROM Windows 7 (OS I use). A way to download it in W7 (so far I've only seen instructions on downloading from Ubuntu itself).

I want to study the code and see how it works.

Please tell me how! Thank you!

---

### Post by spiky001 on 2011-10-03
Will this help [http://askubuntu.com/questions/2964/where-can-i-find-the-source-code-for-the-ubuntu-kernel](http://askubuntu.com/questions/2964/where-can-i-find-the-source-code-for-the-ubuntu-kernel)

---

### Post by ramosdelpalo9 on 2011-10-03
Ok, I got stuck here. [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-natty.git;a=summary)
Say to see the 11.04 kernel.

What specific file do I download?

---

### Post by WorMzy on 2011-10-03
> **ramosdelpalo9 said:**
> For what I understand, Ubuntu is the main Unix-like OS others are based on. In other words, that Kubuntu, Mint, Xubuntu, etc. are Ubuntu-like OS.

Nope.

Ubuntu, Kubuntu, Xubuntu, etc. all use the same kernel (well, assuming you don't install them all to separate partitions and pick and mix between 32-bit and 64-bit, PAE, generic and server, and the rest of that)

Mint, however *is* based on Ubuntu. I'm not sure whether they use the same kernel as the *buntus, but it is one of only a handful of distros which is actually based on Ubuntu.

Ubuntu itself is actually based on Debian.

Check out [this nice linemap of Linux distros]("http://www.markus-gattol.name/misc/mm/si/content/linux_distro_timeline.png"). It's a bit out of date (circa 2007), but it should give you an idea about just how many distros there are out there, and how few of them are related to Ubuntu.

If you want to look at the actual Linux kernel source code, look here: [https://github.com/torvalds/linux](https://github.com/torvalds/linux)

---

### Post by ramosdelpalo9 on 2011-10-03
Great! I did not knew if it could be available, but I was looking more specific for the Linux kernel.

Anyway, thanks for the rest of the info. Was helpful to understand. I'll read the ReadMe file.

---


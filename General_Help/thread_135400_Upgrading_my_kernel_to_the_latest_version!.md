---
title: "Upgrading my kernel to the latest version!"
date: 2006-02-23
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-02-23
Hello

I am interested in installing the latest kernel, for security and stability issues, and of course just for the fun of it!

so if anyone knows hot to do this, or knows a website that has the instructions , please help me, Thnx.

---

### Post by evilgold on 2006-02-23
```
sudo apt-get install linux-386
```

or linux-686 for PentiumII and above
or linux-k7 for Athlon and above
...there are some others that i dont remember

Ubuntu should automatically upgrade to the newest kernel anyways though.

If you want you can go to kernel.org and download the plain vanilla kernel and compile it yourself. There are a few guides on kernel compiling here, just search it.

---

### Post by Strike&gt;&gt; on 2006-02-23
Thank you for your help. but ubuntu hadn't upgraded it for some reason, i did what you told me and upraded it. but wats the difference between vanilla kernel and the regular kernal?

---

### Post by evilgold on 2006-02-23
Short explination: A vanilla kernel is a regular kernel. The kernel you get with ubuntu has various patches and additions to it, like say added drivers or hardware support.

More detailed: You would use a vanilla kernel if say you wanted to add a patch that wasnt provided by ubuntu, or you just wanted a more optimized kernel. For example, I have a custum kernel thats optimized for K7 (athlon) and has only support for the hardware in my computer, so my kernel is a lot smaller and a bit faster then the standard 386 kernel that comes with ubuntu, but if i where to boot it on another computer (say a PentiumII) it wouldnt operate properly. Where as ubuntu's kernel will run on anything above a 386 (technically speaking, i wouldnt really run it on anything less then a PII)... 

I wouldnt reccomend compiling a kernel from vanilla unless you have a reason to (or just want to learn how to), but you should upgrade to your processor type kernel, it will speed things up a little bit(like boot up).

---

### Post by Strike&gt;&gt; on 2006-02-23
Wow, you just answered so many of my questions, Thanks a lot.

but you see the problem is i have a p4 machine which means i should be using 686, but due to ati, or other drivers, i have to stick to 386.:(  but i can't  wait until dapper comes out, hopefully ati and other comapnies would support it.

---

### Post by evilgold on 2006-02-23
You should be able to get the 686 kernel to work with ati drivers just fine. Try it and see if it works. If not the 386 kernel is still bootable from grub also.

---


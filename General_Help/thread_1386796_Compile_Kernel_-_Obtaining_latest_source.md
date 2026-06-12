---
title: "Compile Kernel - Obtaining latest source"
date: 2010-01-21
forum: General Help
---

### Post by kenm_uk on 2010-01-21
I have recently compiled my first kernel using an Ubuntu 9.10 (karmic) installation on a VirtualBox.  I followed the instructions at:
[http://easylinuxcds.com/blog/?p=3244]("http://easylinuxcds.com/blog/?p=3244")

These instructions involved using the source from
```
apt-get install linux-source
```

On my machine,
```
uname -a
```
returns
```
Linux bluemoose 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
```

**My question is: how does "2.6.31-17-generic" relate to the source in "linux-source"?  Is the source code in "linux-source" the same as the most up-to-date official Ubuntu kernel (in my case 2.6.31-17-generic)?  If Ubuntu releases an updated kernel, how/where do I obtain the updated source so that I can make my kernel changes and re-compile?**

Thanks,
Ken

P.S. The reason I am trying to compile my own modified kernel is to incorporate the fixes for the Ortek Wireless Keyboard:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405390]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405390")
[http://bugzilla.kernel.org/show_bug.cgi?id=14787]("http://bugzilla.kernel.org/show_bug.cgi?id=14787")
while at the same time trying to keep my system as close to the official Ubuntu 9.10 kernel as possible.

---

### Post by kenm_uk on 2010-01-28
I recently discovered this useful link:
[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

---


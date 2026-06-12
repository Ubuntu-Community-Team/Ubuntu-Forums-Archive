---
title: "Compiling a kernel =&gt; root fs won't mount"
date: 2010-05-16
forum: General Help
---

### Post by meklu on 2010-05-16
So, I'm trying to compile a "faster", more optimized kernel. It compiles ok, but can't mount the root filesystem. [Here]("http://meklu.webege.com/kernel-conf") is my kernel configuration for the 2.6.33.4 kernel. My boot partition is ext4 on a two-disk FakeRAID array totaling 1TB.
When trying to boot in recovery mode, it says I could mount /dev/sdaX, etc. but can't recognize my dmraid array. BTW, I have no initrd.

---

### Post by meklu on 2010-05-19
*bump*

---

### Post by 3Miro on 2010-05-19
I have recompiled several kernels in the past and this happens sometimes. You have probably disabled some option in the file system/partition part of the kernel. Try recompiling again, but don't change as many things as you did before.

---

### Post by meklu on 2010-06-25
*bump* Updated my first post. Ideas, anyone?

---

### Post by happyhamster on 2010-06-25
Perhaps this issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575666](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575666)

Or this one (posts 1447 - 1450):
[http://ubuntuforums.org/showthread.php?t=311158&page=145](http://ubuntuforums.org/showthread.php?t=311158&page=145)

Good luck.

---


---
title: "Ext4 Data Corruption fix - how to use it?"
date: 2009-07-20
forum: General Help
---

### Post by OobNosferatu on 2009-07-20
I have Jaunty 64bit and it crashes often. It wasn't so with 8.10. This version has been one of the most unstable filesystem/OS combo since windows 95 for me... but I still lurve ubuntu! muahahaha... bring on the pain!

But my noobness apart, I searched for a fix for the severe data loss I keep getting after every hard reboot and sometimes after a regular reboot. 

Here's what I found:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all)

A gentleman says that alloc_on_commit will fix the problem and has been backported to the kernel I'm using (2.6.28-14)... but I don't know where to put that? In my fstab? 

Can someone tell me where this should go?

PS: My home dir is on a separate hard drive...

---


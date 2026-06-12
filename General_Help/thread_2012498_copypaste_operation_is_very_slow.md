---
title: "copy/paste operation is very slow"
date: 2012-06-29
forum: General Help
---

### Post by malikge on 2012-06-29
Hi,
I am using dual boot, window7 and ubuntu 10.04 for quite some time now.
This morning all of a sudden, when I boot into ubuntu it does not boot, and give message that:
> mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _After doing a quick search on ubuntu forum I found this link:
> [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)After trying that every thing went well, and now I am able to boot into ubuntu.

But after that, when I mount the window file system and try to paste some data or try to copy some data from window's partition, then this process is very slow.
Before this problem I get almost 22MB/sec speed when copy/paste data, but now I only get 5MB/sec. and in the middle of the copy/paste operation my system freezes and stops working.

Any ideas why this is happening?

---

### Post by malikge on 2012-06-29
One more thing,
the solution mentioned at:
> [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#comment-form](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html#comment-form)is this permanent solution or not? because now I when I try to boot into ubuntu it gave the same error:
> mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) _

---


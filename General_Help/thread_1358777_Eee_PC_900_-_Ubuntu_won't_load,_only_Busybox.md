---
title: "Eee PC 900 - Ubuntu won't load, only Busybox"
date: 2009-12-18
forum: General Help
---

### Post by E Gardner on 2009-12-18
Hello-

My (pretty limited) knowledge of linux is at a loss here. Any help is greatly appreciated!

I have an Eee Pc 900 with ubuntu 9.04 NBR installed. Everything worked fine for months until about a week ago, but now the OS refuses to boot.

When the machine turns on, I see the splash screen like normal. However, before I get to a login screen, I'm dumped back to the command line and into a "busybox" shell.

I figured I'd just have to re-install the OS, but when trying to boot from a prepared USB stick (with 9.10 installed on it), I get the same error! The only thing that changes is the busybox version.

When attempting to boot normally (not from the USB stick), I see the following error message:

```
Boot from (hda0,0) ext3     d7e1e621-1709-4912-9668-3c34b477dadb
Starting up...
Loading, Please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/[string of numbers here] = dev (8,5)
kinit: trying to resume from /dev/disk/by-uuid/[string of numbers here]
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/[another string of numbers] on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in-shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

---

### Post by dcstar on 2009-12-18
> **E Gardner said:**
> 
........
When attempting to boot normally (not from the USB stick), I see the following error message:

```
Boot from (hda0,0) ext3     **d7e1e621-1709-4912-9668-3c34b477dadb**
Starting up...
Loading, Please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/[string of numbers here] = dev (8,5)
kinit: trying to resume from /dev/disk/by-uuid/[string of numbers here]
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/**[another string of numbers]** on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in-shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

If the highlighted areas do not all have the exact same string, then that is the problem.

---


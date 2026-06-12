---
title: "Hard Drive Appears Dead"
date: 2010-09-08
forum: General Help
---

### Post by Dark Aspect on 2010-09-08
Hello,

I was using Ubuntu today and the entire operating system froze up; upon reset I found that I could not boot into Ubuntu and was greeted with this message:

```
mount: mounting /dev/disk/by-uuid/{uuid} on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file ot directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

At first I assumed the data was okay on the drive since the hard drive shows up in the bios. However, when I booted the livecd things took a turn for the worst when I found I could not mount the drive. The drive is ext4 and is a seagate.

[IMG]http://img195.imageshack.us/img195/18/screenshoterror.png[/IMG]

Now the drive shows up with df -h on the livecd. Any ideas?

---

### Post by oldos2er on 2010-09-08
If you have a LiveCD you might try running fsck on it.

---


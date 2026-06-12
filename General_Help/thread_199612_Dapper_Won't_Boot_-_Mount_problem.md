---
title: "Dapper Won't Boot - Mount problem"
date: 2006-06-19
forum: General Help
---

### Post by Grundlebug on 2006-06-19
So I'm posting this solution in case anyone else has the same problem.  And because I'd like to know if anyone has a solution that I can use to prevent this problem from happening to me again.

I tried to boot my computer like normal after having shut down from a totally normal session where nothing was installed or updated. But Ubuntu wouldn't mount my file system.  I was getting a "target file system doesn't have /sbin/init" error after several mounting errors.  Then I was dropped into a BusyBox terminal.

Well poking around these two sites helped me fix the problem:

[http://www.ubuntu-es.org/node/12185](http://www.ubuntu-es.org/node/12185)
[http://www.linuxquestions.org/questions/showthread.php?t=446745](http://www.linuxquestions.org/questions/showthread.php?t=446745)

I had to use a live cd to fix this all up.

I mounted my regular hard drive:

mount /dev/hda1

Then chrooted there:

chroot /mnt/hda1

Then I checked my various installed kernels by opening /boot/grub/menu.lst

Then I uninstalled my oldest kernel:

aptitude purge aptitude purge linux-image-2.6.15-20-386

Then I rebooted and everything was fine.

Why is this?  Is my boot partition too small?  I used the default settings during install?

---


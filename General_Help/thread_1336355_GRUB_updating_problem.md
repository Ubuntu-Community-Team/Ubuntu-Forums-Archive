---
title: "GRUB updating problem"
date: 2009-11-24
forum: General Help
---

### Post by zachlac on 2009-11-24
This is a recurring problem, having started a few months ago in 9.04.  Every time a major upgrade (and I'm not sure exactly what that means; I'm guessing a kernel upgrade) is downloaded to my machine, grub fails to boot.  The kernel line is modified so that my disk is referred to by UUID and not name, and this makes the machine not boot.

I'm dual booting XP and Ubuntu.  If I do a "find /sbin/init" from grub terminal, I get (hd0,5).  If I do a "find /boot/vmlinuz-###########" I get (hd0,1).  Thus, setting my root line to "hd0,1" and my kernel line to have "root=/dev/sda6" instead of "root=UUID=############################" fixes the problem.

However, I have to constantly repeat this.  Why is this the case?  I've tried checking the UUID of the partition (hd0,5) and the UUID value that grub rewrites with is correct.  This makes no sense to me.

Thank you for your help.

---


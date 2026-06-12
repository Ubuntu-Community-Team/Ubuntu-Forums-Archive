---
title: "Ubuntu fails to boot"
date: 2011-02-06
forum: General Help
---

### Post by apolishch on 2011-02-06
Hi,

I have been running Ubuntu for about six months on a dual boot system with Windows 7.
Recently, and for no discernible reason, every time I try to boot into Ubuntu, it defaults to a commandline after showing the following error message:

```

mount: mounting /dev/disk/by-uuid/04aa3697-7bc0-45b5-b86a-77a1e6534bd5 on /root failed: invalid argument
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)

```

I tried booting into older versions of the kernel from grub, as well as into recovery mode. This made no difference whatsoever.

After that I put in my Live CD and booted into Ubuntu off CD successfully. 
I then launched gparted, and attempted to check my partitions. Unsuccessfully.
I have tried fsck and e2fsck. Unfortunately, I did not take down the resulting error messages, and now I can't boot via Live CD either. It just hangs.

Finally I tried reinstalling Ubuntu. This froze after the first screen where it verifies that I am connected to power/the internet. I let it hang for about 12 hours hoping something would change. It didn't.

Now I am currently waiting for to boot off CD(mostly so I can take down the error messages). Its been hanging for three hours.

For the record, Windows 7 launches just fine.

I have also attempted to install a different distro (Slax). When I booted up with the CD in the drive, I received a "missing operating system" error, and the machine started beeping incessantly.

Any help/ideas/suggestions would be greatly appreciated.

---

### Post by spaceboy909 on 2011-02-06
:(  Those are signs of hardware issues.  Since you can't even boot from CD now, and you're getting those BIOS error messages like 'non-system disk', etc, plus error code beeps, I'd say it's almost certainly bad hardware.

A couple of long shots you can try while you're waiting for other opinions:  Can you get into the bios menu?  If so, reset to default or optimal settings.  If you can't get into the bios screen, then something on the mainboard is toast, probably the bios at the least.

If you can get in and reset it, then take an extra minute and check that your drive cables are seated good.  I've had loose cable issues in the past so I always recommend that to rule it out.

If you reset your bios, then _don't forget_ to either set it up for a primary CD boot, or manually trigger the menu with F12 during boot (or whatever it is on your system).

---


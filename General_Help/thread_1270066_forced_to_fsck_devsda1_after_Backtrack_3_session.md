---
title: "forced to fsck /dev/sda1 after Backtrack 3 session"
date: 2009-09-19
forum: General Help
---

### Post by Switch08 on 2009-09-19
Hey all, when ever I boot from Grub2 into Backtrack3 everything goes as planed. The problem is when I try to boot back into Ubuntu 9.10 I am forced into having to fsck /dev/sda1

Due to an error: Superblock last mount time.

Any help would be much Appreciated.

Thank you.

---

### Post by blueridgedog on 2009-09-19
Are you booting from the Backtrack CD or have you installed it on your drive?  Is you bios time correct?

---

### Post by Switch08 on 2009-09-19
Thank you blueridgedog for your reply:

Yes that seems to have been the issue. Strange I didn't think time would stop the boot process.

I fixed this issue by:

gksudo gedit /etc/default/rcS

and changing UTC=yes to UTC=no

and lastly reseting: sudo /etc/init.d/hwclock.sh restart

---

### Post by blueridgedog on 2009-09-19
When you booted from the CD, it read the time from BIOS and set the last access time of the inode when it mounted your hard drive.  When you booted Ubuntu, it saw the last access time that was old and scheduled a scan.

---


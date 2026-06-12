---
title: "Server reboots into initramfs after freeze"
date: 2012-07-05
forum: General Help
---

### Post by Zentor on 2012-07-05
Hi
I run a Ubuntu 12 server (kernel 3.2.0-26) and it's worked great for me up until now. I've had a lot of bad weather around here lately and has cause my system to reboot a few times. Each time I've brought it back up fine until yesterday

Booted up all was good and I left it. This morning it seemed to be frozen. no keyboard input would do anything, so I rebooted.

Now it shows this on startup and won't got to log in:

```
mount: mounting /dev/mapper/LinuxOne-root on /root failed: Invalid argument
Begin: Running /scripts/locat-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory.
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
Not init found. Try passing init= bootarg.

BusyBox v1.18.5 (Ubuntu 1:18.5-1ubuntu4) built-in shell (ash)

(initramfs)
```I don't necessarily have to log in if I can someone how retireve a couple files from it as they are very important.
Any help would be greatly appreciated.
I've looked all over these forums and found a couple people with similar problems and attempted their solutions to no avail. Please help

Thank You

---

### Post by Zentor on 2012-07-05
anyone?

---

### Post by Zentor on 2012-07-05
No one has heard of this?

---


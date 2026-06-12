---
title: "GRUB2 not mounting drive??"
date: 2010-06-10
forum: General Help
---

### Post by dvlchd3 on 2010-06-10
I'm having a problem on startup where GRUB seems to time out attempting to mount my main drive.  Here is the error it gives me:

> 
Gave up waiting for root device.  Common problems:
-Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/b1517926-aba4-47d1-81f0-42ca5dd36257 does not exist. Dropping to a shell!


I am given a initramfs shell.  Sometimes waiting a couple of minutes and then typing 'exit' works.  However, I've noticed if I do this:
```

(initramfs) mount /dev/disk/by-uuid/b1517926-aba4-47d1-81f0-42ca5dd36257 /root
(initramfs) exit

```
my laptop will boot.

I'm really not sure what the issue is, or how to even start to resolve it...Any ideas?
I'm not sure what the issue is, since

---

### Post by dvlchd3 on 2010-06-11
Bump

---

### Post by WorMzy on 2010-06-11
Is your /boot on the same drive that's failing to mount?

If it is, then there's a possibility that the drive, after it's been used to load grub, is being treated as a part of a RAID array. I've had a similar problem, and it happened intermittently. The solution was to add "nodmraid" to the kernel boot line in menu.lst (I use grub legacy, I'm not sure how you would do the same thing in grub 2).

You should be able to temporarily add the nodmraid argument to the boot options when you first boot up. Just enter the boot menu (I believe you need to hold down Shift for grub 2, or Esc for grub legacy), and press "e", move down to the kernel line and press "e" again, then add "nodmraid", okay it, then press "b" to boot.

Sorry if these instructions are hard to understand, I hope you'll be able to understand what I mean. :)

---


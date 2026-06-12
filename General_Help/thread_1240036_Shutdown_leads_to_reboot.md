---
title: "Shutdown leads to reboot"
date: 2009-08-14
forum: General Help
---

### Post by dreamedge on 2009-08-14
Hey!

I've installed ubuntu 9.04 on a Asus Pro50G laptop.
Everything works great except shutdown.

When I shutdown the computer, it reboots. So far I've tried:


[LIST]
[*]acpi= off
[*]acpi = force
[/LIST]

I've also looked at the bios settings, but unfortunately the bios doesn't have any settings for ACPI. I've also googled on this and I found an exact match on my problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234700](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234700)

But as you can see, it states that the problem was fixed in 8.10.. But now it's apparently back.


So does anyone have any ideas/suggestions on how to move on, should I file a new bug report at launchpad for 9.04?


I can post the dmesg and/or syslog log if it's needed.


Thanks for any reply..


Update: I've solved the problem by upgrading the kernel to 2.6.30.

---

### Post by P4man on 2009-08-14
it amazes me how often old bugs turn up again.
got a few bugs that took a year or longer to get fixed, and a few months later you do an update and its back again lol.

anyway, good yours is fixed again in 2.6.30.

---


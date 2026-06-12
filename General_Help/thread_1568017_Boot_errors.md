---
title: "Boot errors"
date: 2010-09-04
forum: General Help
---

### Post by a sandwhich on 2010-09-04
Hey, I am dual booting Ubuntu and windows, the grub screen is posted below. I can boot into the third option down, but when I try to boot into the first option, it returns the below errors. It also does that when I try the recovery option. What does this mean and how can I fix this?

udevadm trigger is not permitted while udev is unconfigured.

Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)

-Check rootdelay= (did the system wait long enough?)

-Check root= (did the system wait for the right device?)

-Missing modulles (cat /proc/modules; ls /dev)

ALERT! /dev/disk/byuuid/7dd5ed87-b63d-4dcd-89e7-5e6e8c3a009 does not exist. Dropping

to a shell!

 

Buys Box built in shell

enter help for commands

 

(initramfs)

---

### Post by Rubi1200 on 2010-09-05
It probably means there is some issue with that kernel version and, most likely, your hardware.

You highlighted recovery mode in the screenshot, but can you boot into that kernel there normally?

What graphics card do you have installed?

What version of Ubuntu is this?

---


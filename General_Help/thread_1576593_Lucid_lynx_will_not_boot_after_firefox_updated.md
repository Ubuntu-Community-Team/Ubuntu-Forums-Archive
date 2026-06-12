---
title: "Lucid lynx will not boot after firefox updated"
date: 2010-09-17
forum: General Help
---

### Post by phobophilia on 2010-09-17
Problem occurred after attempting to update firefox and configure evolution. Attempted to update firefox last night, it froze, attempted to open the system monitor to end the unresponsive process, and got a message saying the system was unable to support a new process because it couldn't fork. Did a forced reset, and the following now happens upon starting up. 

After selecting ubuntu (as it's a dual boot system with Windows XP) at the grub loader, blank screen, to this:

```
mount: mounting dev/disk/by-uuid/5b24d4b5-9b8d-4608-9387-0d92756dcdd8 on root
failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed:no such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

```

It will not run recovery mode, and I have no bloody idea what it means by init=bootarg. Help please?


EDIT: Nevermind- I'm going to try the methods listed in [http://ubuntuforums.org/showpost.php?p=9411005&postcount=2](http://ubuntuforums.org/showpost.php?p=9411005&postcount=2) , and hope the gods of fsck smile upon my lowly hard drive.

---

### Post by zazootheparrot on 2010-10-14
Hello there,

I have an ubuntu 10.04 Lucid Lynx running on a Sony Vaio VGN-SZ740.  During the past week I've had a problem with the operating system  booting. It happened after I did the usual update of the system using  the update manager.
It's worth mentioning that I have a Linux/ Windows 7 dual boot but they  all worked fine before. Here's what I see in the GRUB page when I start  my computer:
```
GNU GRUB version 1.98-ubuntu 7
Ubuntu, with linux 2.6.32-25-generic
Ubuntu, with linux 2.6.21-25-generic (recovery mode)
Ubuntu, with linux 2.6.21-24-generic
Ubuntu, with linux 2.6.21-24-generic (recovery mode)
Ubuntu, with linux 2.6.21-23-generic
Ubuntu, with linux 2.6.21-23-generic (recovery mode)
Ubuntu, with linux 2.6.21-21-generic
Ubuntu, with linux 2.6.21-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest console 115200)
Windows 7 loader (on/dev/sda1)
```After I choose the first one (as I always did), I get the following:
```
Ubuntu 10.04.1 LTS ava-laptop tty1
ava-laptop login .. [129.736043] tpm_tis 00:09: tpm_trasmit :tpm_send:  error 42 94967234
```and then it takes more that 3 minutes for ubuntu  to come up!!!

I would we grateful if anyone could could help me solve this issue,

Thank you in advance

---


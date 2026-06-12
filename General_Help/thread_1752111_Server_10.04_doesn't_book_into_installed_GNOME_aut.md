---
title: "Server 10.04 doesn't book into installed GNOME automatically"
date: 2011-05-07
forum: General Help
---

### Post by kingcu on 2011-05-07
I've installed Ubuntu server 10.04 and then installed Gnome desktop on top of it, because I am new to Linux and its command line, I need the GUI desktop to help me get around. However, the problem I got is that the server doesn't boot into the GUI desktop when powered on. It's booting into a shell like this:

```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enought?)
   - check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/cecdata-root does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```I ran the first cat command and got:

```
result of (cat /proc/cmdline)
BOOT_IMAGE=/vmlinuz-2.6.32-28-server root=/dev/mapper/cecdata-root ro quiet
```Then I have to type "exit" to exit the shell and it then boots into the GUI desktop. Any idea what's wrong?

---


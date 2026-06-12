---
title: "Windows virus destroyed Ubuntu"
date: 2011-05-10
forum: General Help
---

### Post by Fritz The Rat on 2011-05-10
That's what appears to have happened. I hit a site that started running a fake virus scan and FF wouldn't let me out of it so I hit the power button and chose "Reboot" from the menu. That's the last I saw of Ubuntu. Now it comes to what appears to be a boot menu and hangs. Last two choices on the list are Memtest.

I have no idea how to recover from this so any help much appreciated.

---

### Post by ajgreeny on 2011-05-10
Boot to tyhe live CD "Try ubuntu" option, then from that run terminal and use command ```
sudo e2fsck /dev/sdx#
```where sdx# is your ubuntu partition, eg /dev/sda1.

If that sort of thing happens again use **AltGr+Print Screen+K** to kill the GUI desktop, and take you back to a login screen.

---

### Post by WorMzy on 2011-05-10
You probably caused the filesystem to become corrupted when you hard reset your machine. Follow ajgreeny's instructions to fix it.

---

### Post by deconstrained on 2011-05-10
First, gather some diagnostic information:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Unix-based operating/files systems are generally quite robust, and killing the power shouldn't damage it, but if the initial ramdisk and init scripts (what gets unpacked into memory and executed when it starts up) won't run filesystem checks before mounting, you'll need to use fsck (file system check) on the hard drive partitions manually.

---

### Post by Fritz The Rat on 2011-05-10
Thanks all. I managed to get back in by using two commands I found here to reinstall Grub2. I'm still getting an error message about incorrect syntax when it first starts to boot but once in everything seems to be working normally. I'll follow your instructions, ajgreeny as soon as I get to a stopping point. Maybe it'll fix the syntax errors.

What really happened is I reacted like I would have had the OS been Windows. I now know I had nothing to fear from this but in the panic of the moment, I just wanted to kill it and I killed it the wrong way. But still, when I hit the power button, I got a shutdown menu and chose reboot from it so it's not like I pulled the power cord.

---

### Post by Habitual on 2011-05-10
alt+F2 then
```
xkill
```
and point cursor at offending program.

---


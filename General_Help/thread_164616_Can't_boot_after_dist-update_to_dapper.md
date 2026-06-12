---
title: "Can't boot after dist-update to dapper"
date: 2006-04-23
forum: General Help
---

### Post by XPiS on 2006-04-23
After [FONT="Courier New"]apt-get dist-update[/FONT] to Dapper the loader can't mount root file-system in normal boot (and recovey as well). 

[B]ALERT! /dev/sda7 does not exist. Dropping to a shell!

BusyBox v1.01 (Devian 1:1.01-3ubuntu6) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off[/B]

I'm using upgrade mode 'cause the Dapper install cd hangs when booting the kernel (Toshiba laptop). I tried all possible boot options, but Install CD failed to boot.

I've read and searched through out the forum. The only thing I managed to do is booting from ubuntu 5.10 live cd and

[B]sudo -s
mount /dev/sda7 /mnt
chroot /mnt
[/B]

One more thing.
In my /boot folder is only one kernel - 2.6.12-9-686

What can I do now???

---

### Post by cocox on 2006-05-15
maybe this can help you, good luck

[http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808](http://www.ubuntuforums.org/showthread.php?p=1017808#post1017808)

:mrgreen:

---


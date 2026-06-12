---
title: "Ubuntu 12.04 Grub2 - Not Updating?"
date: 2012-04-27
forum: General Help
---

### Post by A4orce84 on 2012-04-27
Hello Everyone,

I recently installed Ubuntu 12.04, and have been messing with Grub2 to clean up my boot-loader menu a bit.

However, it seems that any updates I make to: "sudo vim /etc/default/grub" are not taking affect. I'm making sure I perform a "sudo update-grub" after making any changes....but nothing is working.

Just to add, I was messing around with the "burg boot-loader" and uninstalled it, and now I'm faced with grub not updating....

Any change I make does not seem to work at all! Changing the default OS, time for boot options, etc....nothing is taking affect.

If anyone could help me out, I would greatly appreciate it.

Thanks,


--Asif

---

### Post by kipjones on 2012-04-27
+1.  Installed 12.04 today, edited /etc/default/grub, and then here's what I get:

```

noelle@noelle-ubuntu:~$ sudo update-grub
[sudo] password for noelle: 
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: options: not found

```

Any advice would be appreciated.

---

### Post by garvinrick4 on 2012-04-27
Use a Live CD and chroot into your install and purge and reinstall grub.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---


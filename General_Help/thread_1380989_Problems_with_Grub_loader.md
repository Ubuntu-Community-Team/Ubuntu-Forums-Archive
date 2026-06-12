---
title: "Problems with Grub loader"
date: 2010-01-14
forum: General Help
---

### Post by Dynux on 2010-01-14
Hi all, i've a little problem with the grub loader. I've two OS in my laptot: Ubuntu 9.10 Karmic Koala 64bit and Windows 7 64bit. 
But i can't boot Windows 7 from the grub loader.
The grub still load the /dev/sda1 partition that is the recovery partition of the laptot, while windows 7 is in the partition /dev/sda6. 
I tried to modify the path in the grub.cfg, but still load the wrong partition, how i can do? Please help me, thank you.

---

### Post by Leppie on 2010-01-14
you modified the path in grub.cfg? how did you do this? the menu entry should be something like this:
```
menuentry "Windows 7" {
set root=(hd0,6)
chainloader +1
}
```

remember that windows operating systems like (i.e. need to be/have to be) on primary partitions. sda6 is in the extended partition, so this may prevent 7 from booting.

---

### Post by drs305 on 2010-01-14
Did you make the change to /etc/default/grub and then run "sudo update-grub" to make the change take effect?

See if this helps you, if it is just a menu selection problem and not something more serious.
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---


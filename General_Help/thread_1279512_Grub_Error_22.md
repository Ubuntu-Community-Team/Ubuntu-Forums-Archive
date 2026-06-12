---
title: "Grub Error 22"
date: 2009-09-30
forum: General Help
---

### Post by cdmike2k8 on 2009-09-30
Hello
On starting my system, I am getting Grub Error 22.  I followed the steps in [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351"), and it did not work.  The first time I ran the command ```
find /boot/grub/stage1
```, it found (hd0,0) as well as (hd1,0).  I followed the rest of the steps, choosing (hd0,0).  When I restarted, it did not work, and I still received Grub Error 22.  I then went back in and tried to do the same steps again, except it said file not found.  I then followed the steps in the lower part of the thread with all the mounting commands, and after those commands, changing /dev/sda6 to /dev/sdb1 (my boot hard drive), I was able to find both of the hard drives with the find command.  I then proceeded to use (hd1,0) and follow the commands.  This, as well, was not successful.  If anyone could help, I would really appreciate it, as I do not want to have to reinstall.  I am currently on a laptop w/o linux.

---

### Post by oldfred on 2009-10-01
Error 22 says partition does not exist. Did you edit partitions so the settings are looking for the wrong locations?
[http://members.iinet.net.au/~herman546/p15.html#22](http://members.iinet.net.au/~herman546/p15.html#22)

I would first try supergrub to correctly install grub. Download and create a CD
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---


---
title: "[and 64bit ubuntu] - Gave up waiting for root device"
date: 2010-06-18
forum: General Help
---

### Post by AndrewRenn on 2010-06-18
Hello all!

Well, I had to reinstall 10.04 because I got an error, waiting for root device. And I figured I knew why I got this error:

I changed my xconf.cfg (or whatever the file is in /etc/x11/) -- So this time I downloaded the 64 bit, because I have a 64 bit computer, so though, might as well get it!

I've narrowed the problem down to this:

After I install nvidia settings (the x server or whatever?) And change my view to TwinView (I have my laptop monitor and an external monitor), and save the config file, this happens. I will do some more testing, but here is the whole error message:

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system not wait long enough?)
   - Check root= (did the system wait for the right device?
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/bcb49367-8554-4116-8e4d2b39d92415cf does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.



Hope you guys can help..!

Thanks,

Andrew

---

### Post by AndrewRenn on 2010-06-18
Still need help :(

I endeed up getting a grub error after I deleted the ubuntu partitions, and had to do special stuff to make Win 7 work again, and now its saying its an illegal copy (which it is, lol!), but I don't care if it says that, because I want to use ubuntu as my main system from now on, but I get that error everytime I try to fix my monitors for the external to be the main one

---


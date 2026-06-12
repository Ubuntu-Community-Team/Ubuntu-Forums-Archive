---
title: "TTY's"
date: 2010-07-20
forum: General Help
---

### Post by Danamatan on 2010-07-20
Hi, 
I am running ubuntu 10.04
I am trying to access the tty's
When I hit Ctrl + Alt + F1 I get a screen that says:
FATAL: Error inserting uvesafb (/lib/modules/2.6.32-23-generic/kernel/drivers/video/uvesafb.ko): unknown symbol in module, or unknown parameter (see dmesg)

Ctrl + Alt + F2-F6 all I get is a flashing cursor that won't do anything

Any ideas?
Thanks,
Dan

---

### Post by theOGRE on 2010-07-25
Have a looksy at my post : [here]("http://ubuntuforums.org/showthread.php?t=1513557")
I still haven't found a solution to my problem, but my tty's work now. In the end I decided to keep my kernel line in /boot/grub/menu.lst without 'splash' or 'quiet'. Hope it helps. If it does, I still don't get it! ](*,)

---


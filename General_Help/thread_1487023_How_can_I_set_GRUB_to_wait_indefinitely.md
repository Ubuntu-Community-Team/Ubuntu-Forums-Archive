---
title: "How can I set GRUB to wait indefinitely?"
date: 2010-05-18
forum: General Help
---

### Post by zami on 2010-05-18
When I reboot, I just want GRUB to wait for my input, rather than have a countdown timer until it starts up the default OS.

How can I set this?

The answer is not 
System> Administration> Start-Up Manager
that is handy, but you can only set the timer from 0 - 100 seconds.  

Thanks for any help!

-zami

Edit: 
Whoops!  I'm using Ubuntu 10.04, Lucid.  A fresh install.  I have no idea what version of Grub it's using.
(I read somewhere to do "grub --version" but got the message "The program 'grub' is currently not installed...)
-zami

---

### Post by plucky on 2010-05-18
> When I reboot, I just want GRUB to wait for my input, rather than have a countdown timer until it starts up the default OS.

How can I set this?


```
gksudo gedit /etc/default/grub
``` and set **grub_timeout** to -1 (minus one),then run ```
sudo update-grub
```


Good Luck

---

### Post by zami on 2010-05-18
plucky - that's perfect.  Thank you!

-zami

---


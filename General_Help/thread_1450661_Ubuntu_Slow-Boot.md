---
title: "Ubuntu Slow-Boot"
date: 2010-04-09
forum: General Help
---

### Post by rocket16 on 2010-04-09
Hello all. I recently install Ubuntu-studio Desktop and some other packages. And, I upgraded my System. But since then, the Grub has started to display (I have only 9.10 installed, using the entire Disk). Also, unless I select the entry, Grub does not automatically start. The startup takes nearly 1.5 minutes. And, the Login screen, after the installation of Ubuntu Studio GDM, is much slower. I removed the Ubuntu-studio GDM package, still it takes about 20 seconds to allow me to enter Username and password. Any idea?

---

### Post by smartidiot on 2010-04-09
Seems like other packages got loaded as well when you installed the Ubuntu-Studio.

Did you check which services start up?  Did you look at the log and see what is taking so long to initialize?

---

### Post by aeiah on 2010-04-09
well, seems like there are two problems.. first is that grub isn't configured right. you probably need to set the default operating system to boot. perhaps a kernel upgrade has done something strange.

to get to the bottom of the other problem you can either scour through /var/log/messages and find what it's doing when it hangs, or install and configure bootchart. this will give you a chart of your boot process, mapping out how long each process takes and hopefully you can then find out what's causing your system to hang.

---


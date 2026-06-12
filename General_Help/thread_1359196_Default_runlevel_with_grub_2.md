---
title: "Default runlevel with grub 2"
date: 2009-12-19
forum: General Help
---

### Post by GagleKas on 2009-12-19
Hi.

How can I configure default runlevel with grub 2?

I have ubuntu 9.10, so the file /etc/inittab does not exist. Also, upstart configuration file /etc/event.d/rc-default does not exist. So I have to edit the default runlevel with grub, BUT the file /etc/grub/menu.lst does not exist because GRUB has upgrated to GRUB 2. Damn!!!!

How can I edit the default runlevel??

Thanks.

---

### Post by Ganton on 2010-02-11
Maybe what it's wanted is to boot (K)ubuntu in text mode, in this case:

Execute
```
sudo nano /etc/default/grub
```

Find
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and change it, leaving it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"

Execute:
```
sudo update-grub
```

Later, if you want to go into the graphical mode, you can execute:
```
startx
```

---


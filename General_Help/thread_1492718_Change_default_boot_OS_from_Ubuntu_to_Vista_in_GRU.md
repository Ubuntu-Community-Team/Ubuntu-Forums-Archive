---
title: "Change default boot OS from Ubuntu to Vista in GRUB"
date: 2010-05-25
forum: General Help
---

### Post by cjschrissouth on 2010-05-25
Hi,
I'm extreemly new to Ubuntu and installed 10.04 onto a partition this morning. When I boot up my PC a menu called GRUB comes up and the list of OS's has ubuntu 1st. If I dont change my selection to vista it automatically boots into ubuntu. How can I change the order or default booting OS? I have seen other people talk about it but I'm not sure if it's up to date.

Thanks!

---

### Post by James78 on 2010-05-25
Restart your computer, and look at the entries... Imagine it this way... The first entry is 0, the next one is 1, etc. Count up to your Vista entry, and remember the number.

Boot into Ubuntu, then..```
gksudo gedit /etc/default/grub
```Next, edit the entry near the top, named "GRUB_DEFAULT=0", and change the 0 to whatever number the Vista entry was. Then...```
sudo update-grub
```Restart, and Vista will be selected as default, enjoy!

For some help on how Grub2 works, you can read this...
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by philinux on 2010-05-25
> **cjschrissouth said:**
> Hi,
I'm extreemly new to Ubuntu and installed 10.04 onto a partition this morning. When I boot up my PC a menu called GRUB comes up and the list of OS's has ubuntu 1st. If I dont change my selection to vista it automatically boots into ubuntu. How can I change the order or default booting OS? I have seen other people talk about it but I'm not sure if it's up to date.

Thanks!

If you don't want to get into the command line for now then install startupmanager. From software centre, synaptic or this way...
[apt:startupmanager]("apt:startupmanager")

---


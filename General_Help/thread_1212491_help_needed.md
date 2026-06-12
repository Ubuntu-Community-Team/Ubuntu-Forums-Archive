---
title: "help needed"
date: 2009-07-13
forum: General Help
---

### Post by tiajaime on 2009-07-13
hello all, i have some thin clients i wanted to run ubuntu and run terminal client to use remote desktop to windows 2003 active directory terminal services.

the first problem was installing ubuntu since they dont have cdrom and no usb boot support, i installed it by PXE boot, worked perfectly, but only installed base system, so no x windows, then i installed the xwindows with:

apt-get install xorg-window-system

but now i need a window manager and dont know whats the comand to find packages via command line.

what i want is the machines to auto login in the linux system then a lite x window system like fluxbox or lite one to automatcly run the terminal client login window.

can someone guive me some orientation?

many thx in advance

cheers

---

### Post by lisati on 2009-07-13
One way to install a desktop environment when you have only a command line system is through something like this: ```
sudo apt-get install ubuntu-dekstop
```
Note: this CAN result in a big download.

---


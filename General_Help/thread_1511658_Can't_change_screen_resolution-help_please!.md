---
title: "Can't change screen resolution-help please!"
date: 2010-06-17
forum: General Help
---

### Post by dalpets on 2010-06-17
Hi,

I am using Hardy with an Nvidia Geforce 2 MX/MX400 video card & Compaq 7500 monitor. According to windows on my dual boot box, a resolution of 1600x1024 is achievable, however, Hardy is only giving me one res option of 640x480, such that I am unable to print.

When I log into the Nvidia server settings it tells me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server". 
This results in;

xxxx@Aopen:~$ cd /root
xxxx@Aopen:/root$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

Could I please have some help on this problem. Thanks.

---

### Post by srix on 2010-06-17
That should be:
> 
$ sudo nvidia-xconfig


Type in your password if it asks you for one.

---

### Post by dalpets on 2010-06-17
Thanks but that results in the same output.

---

### Post by dalpets on 2010-06-17
Well the matter is resolved-the package EnvyNG did the trick. At least with 800x600 I can now see the print button.
Thanks for your help.

---


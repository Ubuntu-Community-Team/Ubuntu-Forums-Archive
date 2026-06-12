---
title: "NVIDIA incorrect resolution on install"
date: 2010-06-19
forum: General Help
---

### Post by defenestratos on 2010-06-19
Hello,
I have just installed ubuntu 10.04 32 bit on my girlfriend's computer.
She has a NVIDIA GeForce2 MX/MX 400 video adapter and I am having trouble getting the restricted driver working.
First I tried it by the books through the Restricted Drivers assistant under Administration. This was successful but on reboot both the boot screen and the desktop environment were at 640x480. No adjustment using the NVIDIA tools was possible. It said that the monitor was unknown. It is a Fujitsu Siemens D-19.1 monitor. I believe however the problem lies with the graphics adapter because I remember it being identified correctly at some point of the ordeal.
Next I followed a tutorial and removed all of my NVIDIA packages from the computer. I still have my graphical environment though.
After downloading the appropriate (Newer version than that in the Ubuntu repo) driver from the NVIDIA website I entered 
> sudo sh NVIDIA-Linux-x86-195.36.31-pkg1.run file and 
It says that the installation has failed. I can supply log files of the failure if that would be helpful.
Thanks!!!

---

### Post by dino99 on 2010-06-19
i never use .run package because ubuntu devs tweaks and fine tuned our drivers , and they have some good reasons

sudo rm -f /etc/X11/xorg.conf

open synaptic repo and add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by cascade9 on 2010-06-19
The 195.XX drivers are way too new to support the old GF2MX. It needs the 96.XX drivers. 

If you go to the nVidia site to d/l, you should really follow the the drop down menus. (GF2 is under 'legacy' not 'geforce'). 

BTW, the nVidia site for the 96.XX drivers has a mistake. Under 'supported cards' they have- 

> **GeForce 2 series:**
Ti 200, Ti 500, GeForce3

Those are GF3 cards, and they appear to have edited out the GF2 cards by mistake. 

Also, you cant install the drivers with X running, you will need to drop back to a command line only to install the drivers.

---


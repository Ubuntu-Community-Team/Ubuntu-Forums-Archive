---
title: "Problems arised after VirtualBox installation in Karmik"
date: 2010-04-15
forum: General Help
---

### Post by baleks on 2010-04-15
Hi Guys!
I have installed VirtualBox via virtualbox-ose package and it works fine (also installed needed addons), but i can't enable USB on it.

I have karmik release installed, but manual at [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB) did not helps.

I discover 2 problems on my system:

1. It does not have /proc/bus/usb directory and when i try to mkdir it:
```
baleks@BAleks-netbook:~$ LANG=C sudo mkdir /proc/bus/usb
mkdir: cannot create directory `/proc/bus/usb': No such file or directory
baleks@BAleks-netbook:~$ ls /proc/bus
input  pci
```
so my entry in fstab to mount /proc/bus/usb not works :(

Moreover, when i trying to mount that in /dev/bus/usb (althought this directory already exist and with files) mount tells me: mount: unknown filesystem type 'usbfs'

2. virtualbox-ose package does not created user group vboxusers (or any like that) in /etc/group, even after reinstallation of the package.

1 and 2 is two steps to get USB work in VirtualBox, and i don't know what to do.. Attempts to google this problems almost always gets me to the posts/manuals related to older verions of ubuntu, but i have karmik...

Hope somebody helps me.

---

### Post by plucky on 2010-04-15
> **baleks said:**
> Hi Guys!
I have installed VirtualBox via virtualbox-ose package and it works fine (also installed needed addons), but i can't enable USB on it.

I have karmik release installed, but manual at [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB) did not helps.

I discover 2 problems on my system:

1. It does not have /proc/bus/usb directory and when i try to mkdir it:
```
baleks@BAleks-netbook:~$ LANG=C sudo mkdir /proc/bus/usb
mkdir: cannot create directory `/proc/bus/usb': No such file or directory
baleks@BAleks-netbook:~$ ls /proc/bus
input  pci
```
so my entry in fstab to mount /proc/bus/usb not works :(

Moreover, when i trying to mount that in /dev/bus/usb (althought this directory already exist and with files) mount tells me: mount: unknown filesystem type 'usbfs'

2. virtualbox-ose package does not created user group vboxusers (or any like that) in /etc/group, even after reinstallation of the package.

1 and 2 is two steps to get USB work in VirtualBox, and i don't know what to do.. Attempts to google this problems almost always gets me to the posts/manuals related to older verions of ubuntu, but i have karmik...

Hope somebody helps me.


Virtualbox-ose does not support USB. See [Here](http://www.virtualbox.org/wiki/Editions)

Use the package downloaded from the Sun Virtualbox site.

Also Virtualbox questions should go [Here](http://ubuntuforums.org/forumdisplay.php?f=308)

Good Luck

---

### Post by baleks on 2010-04-16
Wow, installing non-free version helps! Thanks ;)

---

### Post by Benbow on 2010-04-16
Apologies for chipping in on your thread and I had the same problem but after installing from the VB site, it is there on synaptic but whin I try to run it with the terminal it tells me that it is not installed. What am I doing wrong?

---

### Post by baleks on 2010-04-16
> **Benbow said:**
> Apologies for chipping in on your thread and I had the same problem but after installing from the VB site, it is there on synaptic but whin I try to run it with the terminal it tells me that it is not installed. What am I doing wrong?

I Don't know. I installed from the non-free repository version 3.1 via synaptics, and run VirtualBox command via Alt-F2 for example and all fine.

---


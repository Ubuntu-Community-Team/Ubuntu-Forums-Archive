---
title: "Help with boot: &quot;init&quot; argument"
date: 2011-09-05
forum: General Help
---

### Post by jarotek on 2011-09-05
I would like to install KUbuntu on an USB stick where I already have GRUB (i.e. not GRUB2) and Puppy Linux.


At this moment, file menu.lst is as follows:

```
default 0
timeout 15
#
# KUbuntu menu entry
title KUbuntu
root (hd0,1)
kernel /casper/vmlinuz root=UUID=<uuid> ro quiet splash
initrd /casper/initrd.lz

```
where <uuid> is replaced with the UUID of the (hd0,1) partition, in which I have copied the contents of the KUbuntu 10.04.3 ISO file.

When I reboot the PC, it shows up a pink splash screen... [http://scr3.golem.de/screenshots/1003/ub_1004b1/thumb480/01_ubuntu_1004_beta.png](http://scr3.golem.de/screenshots/1003/ub_1004b1/thumb480/01_ubuntu_1004_beta.png) (... I can hear the CD drive doing something, though the Live CD is not therein)

... and then it stops booting, and brings me to a BusyBox command line because "No init found. Try passing the init= bootarg."

But I have no idea of what is this parameter, as I am not able to find any documentation or GRUB menu entry examples on the Internet, where it is mentioned. Any help will be appreciated. Thanks.

---


---
title: "CD-ROM not detected- /dev/cdrom does not exist!"
date: 2011-09-30
forum: General Help
---

### Post by verunka5 on 2011-09-30
Hey guys,
I pretty new in Linux and I need your help..
I was unable to install Ubuntu from CD so I've installed it from USB drive.. It seems that CD-ROM wasn't recognized at all...
the things I've checked:

[HTML]root@vera-ubuntu:/dev# ls | grep cd
pktcdvd  
[/HTML]#pktcdvd is directory



[HTML]root@vera-ubuntu:/# lsmod | grep cd
xhci_hcd               72190  0 
[/HTML]#As I've checked it is a module for USB3 devise



fstab:
 [HTML]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8208b5f9-7087-40d5-9e4c-2f483e333a5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9bf73018-8ed3-4ce4-925e-f0a3d549a1af none            swap    sw              0       0
[/HTML]nothing in **lsdev** also...

I am running Ubuntu natty 11.04 , Kernel : 2.6.38-11-generic-pae
I have dual boot with Windows 7 and the CD-ROM works fine there...

Thanks for your help!!

---

### Post by verunka5 on 2011-10-20
The problem solved with 11.10 
10x

---


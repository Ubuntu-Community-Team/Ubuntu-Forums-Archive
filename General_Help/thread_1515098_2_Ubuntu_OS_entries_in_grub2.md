---
title: "2 Ubuntu OS entries in grub2"
date: 2010-06-21
forum: General Help
---

### Post by hengchuen on 2010-06-21
Hi everyone,
 
just as the title, I am using a HP Mini 210 netbook with Ubuntu 10.04 and just started to use Ubuntu yesterday. I am not sure is the problem causing by the recent updates that I did. After the update manager's updates, my grub2 has appear 2 entries of Ubuntu OS and both of them are able to direct me to the OS. Anyone know how to fix it??
 
My grub2 layout current like this
 
Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22 generic (recovery mode)
Ubuntu, with Linux 2.6.32.21-generic
Ubuntu, with Linux 2.6.32.21-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
Window 7 ( loader ) (on /dev/sda1)

---

### Post by Leppie on 2010-06-21
yes, grub2 lists all kernel version installed on your system.
if you only want the newest kernel to show in the menu, open the 10_linux file:
```
gksudo gedit /etc/grub.d/10_linux
```find the next section and add the line in red:
```
list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
[COLOR=Red]list=`version_find_latest $list`[/COLOR]

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
```save and close the file, then run update-grub:
```
sudo update-grub
```from now on, the grub menu will only show the latest kernel version installed on your system. even after newer kernels have been installed by update manager.

---

### Post by metalf8801 on 2010-06-21
> **hengchuen said:**
> Hi everyone,
 
just as the title, I am using a HP Mini 210 netbook with Ubuntu 10.04 and just started to use Ubuntu yesterday. I am not sure is the problem causing by the recent updates that I did. After the update manager's updates, my grub2 has appear 2 entries of Ubuntu OS and both of them are able to direct me to the OS. Anyone know how to fix it??
 
My grub2 layout current like this
 
Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22 generic (recovery mode)
Ubuntu, with Linux 2.6.32.21-generic
Ubuntu, with Linux 2.6.32.21-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
Window 7 ( loader ) (on /dev/sda1)

its because you have 2 different Linux kernels version  2.6.32-22 and the older Linux 2.6.32.21 its a nice to more then one in case theres a problem with the newer kernel like it doesn't work with one of your drivers 
You can remove one of them if you want using Synaptic but I would just leave it

---

### Post by hengchuen on 2010-06-21
I see. Thanks to leppies and metalf. I will leave it there incase the latest kernel has problem then I will use the older one. Good day everyone

---


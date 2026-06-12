---
title: "Old kernel showing in grub2 10.04"
date: 2010-08-08
forum: General Help
---

### Post by ResidentBio on 2010-08-08
I decided to clean my grub2 because it was already showing too many entries

I succeeded to uninstall previous ubuntu 10.04 kernel, but when going for some old ones, i believe related to 9.10, it wont let me. In synaptic package manager they don't even show. I checked the /boot/ folder, and they are there

So if i do this

sudo update-grub i get

Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1

i'm trying to uninstall 2.6.31.-20 and -14 using

$ sudo apt-get remove --purge 2.6.31-14-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-14-*

$ sudo apt-get remove --purge 2.6.31-20-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-20-*

and when i take a look at /boot it shows

vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic

So i'm kinda lost here. Any help would be welcome

---

### Post by Pascal-7 on 2010-08-08
don't know if this helps or not, I tried removing the previous kernels by doing this

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by ResidentBio on 2010-08-08
Thanks pascal, i did try that, but the old kernels i want to unistall do not show for some reason. 

pic

[http://i38.tinypic.com/10de05u.png](http://i38.tinypic.com/10de05u.png)

---

### Post by Ginsu543 on 2010-08-08
Well, according to your pic, you haven't removed all the old kernel image files, so they are still on your /boot folder. In order to remove a particular kernel completely, you need to erase three associated files for that kernel:

1) linux-headers-2.6.XX-XX
2) linux-headers-2.6.XX-XX-generic
3) linux-image-2.6.XX-XX-generic

I usually do this using Synaptic Package Manager. I just type "linux kernel" in the Quick search field, scroll down to where the three packages I want to remove are, and then remove them. Once you have removed the three files, you should run "sudo update-grub" in Terminal to update the grub2 boot list.

---

### Post by sprintexec on 2011-04-14
> **Ginsu543 said:**
> Well, according to your pic, you haven't removed all the old kernel image files, so they are still on your /boot folder. In order to remove a particular kernel completely, you need to erase three associated files for that kernel:

1) linux-headers-2.6.XX-XX
2) linux-headers-2.6.XX-XX-generic
3) linux-image-2.6.XX-XX-generic

I usually do this using Synaptic Package Manager. I just type "linux kernel" in the Quick search field, scroll down to where the three packages I want to remove are, and then remove them. Once you have removed the three files, you should run "sudo update-grub" in Terminal to update the grub2 boot list.

Following Ginsu543's advice worked for me and I was able to regain a useful 1Gb of hd space when I removed six old kernels. Decided to keep the 10.04 LTR. :D

---

### Post by cottfcfan on 2011-04-14
Easy way to do it is install ubuntu-tweak.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Then go to "package cleaner" & "clean kernels" and then "clean config"
Also running update-grub afterwards will do no harm.

---


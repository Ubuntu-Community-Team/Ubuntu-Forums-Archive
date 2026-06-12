---
title: "Multiple installation images on one DVD"
date: 2011-09-16
forum: General Help
---

### Post by firefish5000 on 2011-09-16
I have several installation images such as Debian testing, Ubuntu 10.10, 11.04, 11.10, Xubuntu, Fedora, Linux mint Debian edition, Linux mint 11.04, you get the idea. I can fit several of these on one 3.7 gb dvd but I do not know how to place them on there and then chose which one to boot into at startup. if I burned all the images, would the computer ask which to boot into or would I have to burn them in a specail way, use some program to boot into which gives yyou the option to chose the image? Please help me if you can, I am simply confued. Thanks.

---

### Post by FormatSeize on 2011-09-16
Of course, you can fit each of the iso *files* all onto one DVD, but they will be just files, not bootable images.
 
You have to independently burn images onto seperate disks.

---

### Post by zero2xiii on 2011-09-16
This is possible, but very very difficult.

It involves installing grub to the DVD, then adding the ISO files as bootable options. This must all be done maunaly.

It is possible, but for a seasoned, experienced linux guru. There is to many things that can go wrong, be unclear and cause the whole process to fail.

Rather make a bootable CD/DVD of each individual ISO, or get a 16GB or so flash, and make some 6 partitions, and then setup 6 live linuxes on one flash. That is going to be faaaaar easier.

Cherz

---

### Post by oldfred on 2011-09-16
I use flash drives.

CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

I did it manually but there are many script for multi-ISO on flash drives.
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by firefish5000 on 2011-09-22
Thanks, much better than wasting 3GB of my DVDs.

---


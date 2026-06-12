---
title: "Installing Ubuntu from an ISO file"
date: 2010-06-17
forum: General Help
---

### Post by nemiux on 2010-06-17
Hey everyone,

I'm using ubuntu 9.04, and it was installed in windows, and I gave it only 10 GB of free space. I found that I need more, so I created a 50 GB empty unformatted partition to install ubuntu 10.04 from ISO file:
```
ubuntu-10.04-desktop-i386.iso
```
But I don't want to burn a CD for it. Is there a way to install Ubuntu directly from ISO?

Thanks.

---

### Post by howefield on 2010-06-17
Create a startup disk with a USB stick instead of a CD ?

---

### Post by nemiux on 2010-06-17
No, I kind of need a solution to install from ISO, without writing it to USB or either CD/DVD

---

### Post by howefield on 2010-06-17
> **nemiux said:**
> No, I kind of need a solution to install from ISO, without writing it to USB or either CD/DVD

I haven't tried it but maybe something like this...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> Features

UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. It can load distributions by automatically downloading their ISO (CD image) files, or by using existing ISO files, floppy/hard disk images, or kernel/initrd files, for installing other distributions.

---

### Post by amauk on 2010-06-17
Grub2 can boot off of ISO images stored on local media

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

---


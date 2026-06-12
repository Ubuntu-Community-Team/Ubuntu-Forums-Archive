---
title: "USB boot disk, and boot CD for old bios."
date: 2010-01-31
forum: General Help
---

### Post by squashpup on 2010-01-31
First off, I have to say that I appreciate the efforts of help that I have gotten when I asked this question before, but I don't think many who helped really understood what I was saying.  So, let me say this simply...

I have a USB startup disk, with two partitions.  The first is for file storage, and the second is for the OS.  I did it this way so I could plug it into Windows and transfer files to and from my data partition, because Windows only sees the first partition of a USB disk with multiple partitions. 

Works great, except for one thing.  I sometimes want to boot that USB pen on a computer that won't support booting from USB.  

Used to follow the instructions for making a boot CD here: [http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

I would simply put the USB drive in the computer and start it with the CD.  The CD would boot the kernel and then find the rest of the filesystem on the pendrive. Worked great when the OS was on the only partition or the first partition.  Didn't work at all when the OS was on the second partition.  

So, my question...can anyone make a boot CD for use on a computer that will NOT boot from USB, so that it will find Ubuntu on the SECOND partition of my USB drive and boot it?  

Or maybe does someone know of a free third party app that can be burned to a CD that will find ANY bootable devices and give you the choice of booting them? 

Thanks in advance.

---

### Post by quixote on 2010-02-02
I don't know if Supergrub might do what you want.  [http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems](http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems) and [http://forjamari.linex.org/projects/supergrub/](http://forjamari.linex.org/projects/supergrub/)

---


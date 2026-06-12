---
title: "How do I uninstall Ubuntu?"
date: 2011-08-20
forum: General Help
---

### Post by MagnetsNextToMotherboard on 2011-08-20
Hello, I'm wondering how I can uninstall Ubuntu completely off my computer in order to do a fresh install with the latest version.

The reason I want to do this is because I installed Ubuntu unsuccessfully a while ago, here is two pictures of the error I got, but I took it on an iPod so it may not look good hence the reason I had to take two. Thanks.

---

### Post by Linux_junkie on 2011-08-20
Easiest way is to format the hard drive, or if you've installed it alongside Windows and want to keep Windows then simply format the Ubuntu partition(s) ext4/swap.

---

### Post by 3rdalbum on 2011-08-20
Looks like you've used Wubi to install Ubuntu.

Just use the Windows Add/Remove Programs thingy to remove Ubuntu, and then you can either do a fresh install using the Wubi installer or do a real dual-boot install by booting your computer from the Ubuntu CD. I personally recommend the latter, if you're going to keep Ubuntu.

---

### Post by MagnetsNextToMotherboard on 2011-08-20
Well I just double checked in the uninstall programs part of the control panel and Wubi and Ubuntu is not there. How would I go about deleting the partition?

---

### Post by Mark Phelps on 2011-08-20
> **MagnetsNextToMotherboard said:**
> Well I just double checked in the uninstall programs part of the control panel and Wubi and Ubuntu is not there. How would I go about deleting the partition?

It doesn't have its own partition.  Wubi does not create a partition, instead, it creates a single large file on an EXISTING partition.

If you're still seeing it in the list of boot options, download and install EasyBCD from NeoSmart technologies (presuming you're running Win7 or Vista OS), and use the feature they have to edit the boot entries.  IF Ubuntu isn't listed in the entries, you have a different problem.

---

### Post by MagnetsNextToMotherboard on 2011-08-20
Yep, it's in there. Thank you very much, sir. So I'm guessing I just delete it somehow?

---

### Post by MagnetsNextToMotherboard on 2011-08-20
Ok I tried to install with the CD from boot, but I got this error. (I set my boot device to the CD drive with Ubuntu 64-bit in.)

I can run 64-bit because I have a Phenom II x4 980, 4GB of RAM, and an HD 5770, so I don't understand whats going on. I'm running an MSI motherboard.

Heres the error I got:

"BusyBox V1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)

(initramfs) mount: mounting /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

(initramfs)_"

---

### Post by Mark Phelps on 2011-08-21
> **MagnetsNextToMotherboard said:**
> Yep, it's in there. Thank you very much, sir. So I'm guessing I just delete it somehow?

Yes ... when you run EasyBCD, there's a button containing Edit Boot Menu -- click it.  Then, click the entry you want to remove in the box on the right, click the Delete button, and click Save settings.

It doesn't get much easier than that.

---


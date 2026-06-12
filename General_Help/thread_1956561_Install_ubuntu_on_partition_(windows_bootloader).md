---
title: "Install ubuntu on partition (windows bootloader)"
date: 2012-04-11
forum: General Help
---

### Post by jg2345 on 2012-04-11
I have not had a great deal of experience partitioning a hard drive to install other operating systems, and was wondering how I could go about (in step form if possible) installing ubuntu 12.04 along windows 7.

I want to, however, continue to use the windows boot-loader as opposed to the GRUB boot-loader so have to rule out using the "install alongside other operating systems" option.

Can anyone shed some help on how I could go about this

---

### Post by Nytram on 2012-04-11
I think that Grub is mandatory if you want to boot Linux. Is there any reason why you don't want to use it? If you don't want to partition your drive then you could consider Wubi which installs on your Windows partition, I've not tried it before but believe it uses Grub too during bootup.

---

### Post by PhantomTurtle on 2012-04-11
It is possible not to overwrite the Windows bootloader. Here is a tutorial I used, which is made for 11.04, but works with 12.04(tested by me). [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/"). The only thing I do not do is make a /home partition as it does in this tutorial, but that's up to you.

---

### Post by Mark Phelps on 2012-04-11
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by oldfred on 2012-04-11
I really only know and therefore suggest grub2. But some Windows 7 users have proprietary software with DRM and that can interfere with grub2. Grub did create a workaround for flexnet one of the more popular DRM software vendors used by a lot of the proprietary software.

If you have to have the Windows boot loader, some report this works. It has instructions on its site.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---


---
title: "Install Vista after Ubuntu"
date: 2011-02-26
forum: General Help
---

### Post by MARP1961 on 2011-02-26
I have a 160 GB laptop a with 2GB RAM running Ubuntu 10.04 with no problems. I used to have Vista but removed it completely from my hard drive. I now have three separate partitions: root/, home/ and a 3 GB swap. I would like to reinstall Windows Vista on a dual boot. Can I do this easily without disturbing my Ubuntu install? I would appreciate any advice, many thanks in advance.

---

### Post by TeoBigusGeekus on 2011-02-26
Boot up with a live cd, use gparted
```
gksu gparted
```
to create space for vista and install it.
One thing you have to consider though, is that vista will erase grub, so you will have to [restore]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") it.

---

### Post by seawolf167 on 2011-02-26
[Here]("https://help.ubuntu.com/community/WindowsDualBoot") is a how-to. As usual, don't forget to backup in case something goes wrong! I recommend [Clonezilla]("http://www.clonezilla.org")

---

### Post by TuxIsAwesome on 2011-02-26
Yes, clone your entire drive first.

I can also guarantee that Windows Vista will brutally murder GRUB, you'll need a live cd to reinstall it.

---

### Post by MARP1961 on 2011-02-27
Many thanks for the replies. I have a bootable disk with Rescatux 2.2 on it. Will this be all I need to reinstate grub as bootloader? Also, does it matter where the Vista partition is? Can it go in between the / and /Home partitions if I just shrink the /Home partition to create a new Unallocated space?

---

### Post by patrick_the_fat on 2011-02-27
A better option might be to use Virtualbox, which gives you a full, emulated installation of Windows within Ubuntu, and it supports USB emulation, so you can use it for all the gadget-specific software that is not yet supported in Linux.

Further, you can get Ms Word and Photoshop fully functioning, natively, using your Wine installation.  For everything else, there is Virtualbox.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by oldfred on 2011-02-27
Location on the drive is not important, but it has to be a primary NTFS partition with the boot flag to install. It only installs to empty disks overwriting entire drive or NTFS partitions (like overwriting an XP install). Vista will not see the Linux partitions so be careful about overwriting them. 

Supergrub's  Rescatux should work, but I have not used it. I always like to have a CD or now LiveUSB to repair or boot if there are ever any issues.

---

### Post by MARP1961 on 2011-03-03
Well, after two days I finally seem to have a fully updated Vista installation again. In the end, I did format my unallocated 30GB to NTFS and marked it with a boot flag. Vista installed easily and I managed to pass the online authentication process. However it did destroy Grub. I tried my Rescutux disk but couldn't work out how to use it! In the end, I simply reinstalled Ubuntu 10.04 by leaving my /Home partition untouched and not reformatted but reformatting my / partition. I was delighted to see all my settings preserved and just a few pieces of software to reinstall. All over in less than an hour!

 Vista however then took over two days of fiddling with! Updates, updates and more updates. Drivers to find and install, more updates, configuring updates, installing updates. Service Pack 1, install, more updates.... Service Pack 2 then more updates. When I had finished I then unwisely visited Windows Updates and surprise surprise it presented me with one further update!

Does anyone actually get to use this joke of an operating system? If it hadn't been so time consuming I might be tempted to use gparted and blast Vista away for good. Unfortunately the kids can't play 'Doctor Who' (even with Wine) games or use their beloved iTunes on Ubuntu.

---


---
title: "Change the boot order if startup manager doesn't do it"
date: 2010-05-20
forum: General Help
---

### Post by garrettnixon on 2010-05-20
caveat - I'm just starting to learn Ubuntu and while I appreciate any help, the simpler the better

I'm dual booting with Windows 7 which used to be my default.  In the previous version of Ubuntu I was able to edit the boot order in Grub but a recent update added a few line items to the boot order and shifted the default to Memory test.  With the newer Ubuntu versions my previous instructions for modifying the boot sequence no longer work.  I've set Windows as the default in Startup Manager but it doesn't have any effect.  My boot menu now looks like this:

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

I thought by some great miracle that upgrading to Lynx might get Startup Manager working but the only thing that managed to do is add the following lines on startup:

Mount mounting none on /dev failed: No such device
Chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

...this hangs for a minute or so then some other line flashes too quick for me to read it and everything starts up fine.    

Any suggestions on how to set 7 as the default? (getting rid of the extraneous items wouldn't hurt either, but I'll settle for the quickest and easiest solution)  

Thanks!

---

### Post by Serpher on 2010-05-20
Edit the file /boot/grub/grub.cfg

```
sudo gedit /boot/grub/grub.cfg
```

You'll see blocks of text with the menu titles from GRUB. Just comment those out with a '#' at the beginning of each line.

---

### Post by drs305 on 2010-05-20
garrettnixon,

Welcome to Ubuntu and the Ubuntu forums. :-) You will find this is a friendly forum and we will be glad to help you transition to Ubuntu.

Run this script and post the RESULTS.txt to let us see your Grub 2 setup. If you don't even know how to open a terminal, just let us know.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

In the meantime, you can read up on Grub2 from the links in my signature line. You may not even need to post the RESULTS if you can figure it out from the Grub2 Tasks link below.

---

### Post by Mark Phelps on 2010-05-21
> **Serpher said:**
> Edit the file /boot/grub/grub.cfg

BAD suggestion!!  This file is NOT supposed to be edited -- it says that clearly in the text.

Instead, edit /etc/default/grub

GRUB_DEFAULT=0 is the entry you need to modify.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

---


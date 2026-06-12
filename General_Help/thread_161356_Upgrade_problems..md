---
title: "Upgrade problems."
date: 2006-04-16
forum: General Help
---

### Post by matt1988 on 2006-04-16
Last night I went into synaptic and I hit update. It was a pretty fresh install of Hedgehog other than all of the apache, php, mysql, and some website stuff I put on there. When I woke up this morening after the update overnight it told me that it was finished. When I restart now however it gets to "Uncompressing Kernel" and then reboots. 

It did say that it couldn;t update the kernel but I figured that was normal. Any ideas, I'm fairly a linux noob, I know a little bit around apt-get and such, but not much else.

Thank you in advance.

---

### Post by jpkotta on 2006-04-17
If it says it can't update the kernel, then there's a problem, which has now manifested itself by rendering your system unbootable.

The easy way to fix it is to reinstall and reupdate, and not reboot if there is an error about updating the kernel.  If there is an error, post it here.  The "easy way" is not easy if you have put a significant amount of effort into configuring your system.

If this isn't an option, then you'll need a live CD and a kernel image .deb.  Look for the relevant package on [http://packages.ubuntu.com/](http://packages.ubuntu.com/).  It will be called "linux-image-*version*-*arch*.deb.  Once you have your kernel .deb, put it on a usb drive or a CD, or download it after you've booted the live CD.  Once you've booted the live CD, mount the hard drive, probably with something like ```
mount /dev/hda /mnt
```  Then copy the .deb to your hard drive.  Then, do a chroot ```
chroot /mnt
``` This command basically gives you access to your broken install, as if you were running it instead of the live CD.  Just install the .deb from the chrooted environment ```
dpkg -i linux-image...
```  Unmount the hard drive and reboot ```
exit
cd / ; umount /mnt ; reboot
``` 

Hopefully that will work.  I've done this kind of thing before, but it was a while ago and it wasn't with Ubuntu.

---

### Post by matt1988 on 2006-04-17
I just booted slax off of a usb flash drive and copied some of the things I didn't want to loose and installed breezy badger.  I have to install apache2 php and mysql again but thats no big deal. Thanks for the help anyway.

---


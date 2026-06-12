---
title: "Boot from Flash Drive and Save Programs/settings/files"
date: 2010-08-17
forum: General Help
---

### Post by swraman on 2010-08-17
Hi,

I know it is possible to boot Ubuntu Live from a Flash drive.  But it just boots up and runs like its a CD.  When you shut down the computer, the changes are all lost.

Is there any way to use the flash drive as a Hard Drive?  like install Ubuntu on the flash drive and have the flash drive act as a hard drive - so that if I boot with the flash drive in the computer I can boot of of the flash drive and it would act as a hard drive?

Could I just setup Ubuntu and select the flash drive as the install directory?  would that accomplish this?

Thanks

Raman

---

### Post by oldfred on 2010-08-17
How large is your flash drive? I installed to a 16GB just as a backup and it works. I have not used it a lot.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by swraman on 2010-08-18
Its a 4GB flash drive, but I dont plan on storing many large files on it - just a few apps.

I tried following this tutorial:
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)

and everything seemed to work, but on booting from the usb drive it just goes to a grub command line.
I tried the advice in the comments of the page, and had both grub.conf and menu.lst in the /boot folder, but the same thing happened.

I also had changed the initrd.gz to initrd.lz in the grub.conf/menu.lst files (since in Ubuntu 10 the file is initrd.lz) but the same thing happens!

Any help appreciated - 
Raman

---

### Post by oldfred on 2010-08-18
I copied several ISOs to my 4GB flash drive and use grub2 to boot with loopmount.

What version of grub did you install? Mixing versions of grub often confuses grub. You need to uninstall both and only install one.

The initrd.gz or initrd.lz depends on the version of Ubuntu you are loading. Also only newer versions can be loop mounted.

[http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb](http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb)

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by C.S.Cameron on 2010-08-18
Wow, that tutorial is a chore to follow.
If you have a Live CD just run the create start up disk app.
It will create a bootable flash drive with persistence file, (casper-rw), for you.
If you need more than 4GB persistence you can create a ext2 partition and name it casper-rw.
 
Alternately you can use a Grub2 boot method and make the casper-rw partition for persistence:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)


Or you can just do a full install to USB drive.

It is also possible to add persistence to a Unetbootin install.

---

### Post by swraman on 2010-08-20
Thanks for all the replies!  I wish I found this info out before, a lot of the info out theres outdated.

I actually ended up running the live CD, then installing it to the flash drive and it works great.

I do wonder how long this flash drive will last though, i know the constant reading and writing will lessen its life, but I dont know by how much.

Thanks

Raman

---


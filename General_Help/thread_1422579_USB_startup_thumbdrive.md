---
title: "USB startup thumbdrive"
date: 2010-03-05
forum: General Help
---

### Post by Flexico on 2010-03-05
I have made a startup USB from an Ubuntu LiveCD already, but I was wondering how I might take a high-capacity thumb drive and install a number of different boot disks on it, from an Ubuntu LiveCD to a bootable floppy, and choose one at startup of the disk, kind of like Grub?

---

### Post by Intrepid Ibex on 2010-03-05
I guess it would be as simple as to just partition the usb and use apps like Unetbootin to put different distro images to those different partitions.

It has also been suggested to integrate this with the USB creator: [http://brainstorm.ubuntu.com/idea/23406/](http://brainstorm.ubuntu.com/idea/23406/)

---

### Post by C.S.Cameron on 2010-03-05
NimbleX comes with Vbox and is only a couple hundred MB. 
You can load up and run as many .isos as your disk will hold.
If you have a hard time instaling NX you can achieve the same thing with Ubuntu.
Otherwise you might install your boot disks to the drive, Ubuntu last then mention them in Ubuntu's menu.lst.

As mentioned above Unetbootin, usb-creator or Linux Live might work for installing.

---


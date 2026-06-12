---
title: "Cannot seem to reinstall ubuntu"
date: 2010-08-10
forum: General Help
---

### Post by Jimboted on 2010-08-10
Hi,

Following a catalogue of errors I have decided it is time to reinstall ubuntu from scratch and learn from my mistakes,

However, for some reason, since installing ubuntu the machine will no longer boot from a CD (even if I disable the hard drive in the BIOS it still boots into Ubuntu).

Can somebody please tell me what to do!

---

### Post by abcuser on 2010-08-10
I suggest to look into BIOS, there should be a boot order (or starting order or something similar). And check that there is a CD-ROM in the first place. Then try to power-off your computer manually and turn it on using power button. Maybe you are doing some kind of reboot that is not re-running BIOS from the beginning.

---

### Post by TeoBigusGeekus on 2010-08-10
Ubuntu cannot corrupt your bios...
Try with another cd (windows for example) and test your ubuntu cd on another pc.

---

### Post by yunone on 2010-08-10
BIOS boot order and make sure CD ROM is at the top and first and enabled, depending on your BIOS 

if that doesnt work, try installing from a USB drive

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)




if the USB installs wont work, try this

[http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

---

### Post by wilee-nilee on 2010-08-10
Use the f key prompt for boot from, it appears on the startup screen preboot on your computer, it also tells you the bios key prompt.

---

### Post by Jimboted on 2010-08-10
Hi All,

Thanks for the advice.

Yes, the CDROM is at the top of boot list in the BIOS.  I have even disabled the hardrive in BIOS.

Yes, I have tried a "hard" restart.

Likewise have already tried the windows cd in the machine - doesn't start.  

I have tried both the Windows and Ubuntu CDs in another machine, & yes they both work.

Will try yunone's suggestions next and post results.

ta


Jim

---

### Post by -kg- on 2010-08-10
OK, can you still boot into your present Ubuntu installation?  If so, can your CD drive read the contents of CDs?  It might be a faulty CD drive, considering that the drive is at the top of your boot list in BIOS.

The fact that you can't boot to *any* CD in that machine, but the disks work in other machines points to a hardware malfunction.  If the computer has a USB port and is able to boot to it, you might consider [Unetbootin]("http://unetbootin.sourceforge.net/").

<Edit> One thing about Unetbootin, though...

I have had difficulties with using iso's from the included distributions, which I think was due to corrupted downloads (no md5 checksum check, that I know of).  It would be better to download the .iso (I prefer via torrent for error checking), check the md5 checksum, then use the "Disk Image" selection and point it to the downloaded .iso.  Using this method, Unetbootin has worked flawlessly every time for me.

<Edit #2>  Such a flash drive is also useful for another thing...it's much faster than a CDR, and very useful to, for instance, check to see if the CD Drive is working at all, in case you can't boot into your old Ubuntu installation.

---

### Post by abcuser on 2010-08-11
> **Jimboted said:**
> Yes, the CDROM is at the top of boot list in the BIOS.  I have even disabled the hardrive in BIOS.
It looks like your PC does not recognizes the CD-ROM.

Is CD-ROM drive attached to computer? Have you opened the box and switched some cables?

It is also strange if you disabled hard-disk in BIOS and Ubuntu still boots from hard-disk maybe you didn't disable hard-disk but CD-drive.

Can you post a picture of your BIOS menu settings? (Make a picture with your camera).

---

### Post by Jimboted on 2010-08-13
Hi All,

Managed to put the iso onto a flash drive using UNetbootin.  This has done the job (installed incredibly quickly btw).  New copy up and running & have managed to get the dual monitors working without  damaging my xorg this time.

The booting from CD issue remains, but I will try a different CD drive in the near future to establish whether this is due to a fault.

Once again, my thanks to everyone for their speedy and patient advice.


Jim

---


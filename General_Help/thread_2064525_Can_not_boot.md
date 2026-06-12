---
title: "Can not boot?"
date: 2012-09-29
forum: General Help
---

### Post by googleye on 2012-09-29
Okay so I installed ubuntu from a usb stick and chose to erase everything else completely. Now when I start the computer I get something like no system in hard drive or hard drive error. Only way to boot it up is to do it from the usb stick. Do I need a different bootloader or something?

---

### Post by cogier on 2012-09-29
I suggest that you burn a copy of Ubuntu on to a CD/DVD and try installing from there. I suspect that Grub has not been installed, as you suspected. Not all USB drives are good for this type of work. 

You could boot from your USB drive and sort out Grub but I think it would be much easier to start again with a CD as this is a new install.

---

### Post by googleye on 2012-09-29
Have to wait until I can go buy some dvds then :/ If I check the filesystem there are grub files there though?

---

### Post by jrog on 2012-09-29
It is likely that you installed the GRUB bootloader onto your USB stick instead of the hard drive. To test this, you might see if your system boots with the USB stick inserted. There is a known bug where the installer chooses to install GRUB to the USB stick by default instead of to the hard drive, so, if you don't change that setting during installation, it can easily end up there.

EDIT: Oh, and whether there are GRUB-related files on the hard disk or not, the crucial point is that the GRUB bootloader itself is typically installed in a device's Master Boot Record (not the filesystem), and so is probably on the MBR of your USB stick right now.

---

### Post by Bashing-om on 2012-09-29
googleye; Hi !

To know where grub is installed run these commands from terminal:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub

```and IRT DVD: it is recommended to burn to a cd-r and burn at lowest speed. I have done so many many times, and have yet to experience a problem. (check md5sum).
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by googleye on 2012-09-29
> **jrog said:**
> It is likely that you installed the GRUB bootloader onto your USB stick instead of the hard drive. To test this, you might see if your system boots with the USB stick inserted. There is a known bug where the installer chooses to install GRUB to the USB stick by default instead of to the hard drive, so, if you don't change that setting during installation, it can easily end up there.

EDIT: Oh, and whether there are GRUB-related files on the hard disk or not, the crucial point is that the GRUB bootloader itself is typically installed in a device's Master Boot Record (not the filesystem), and so is probably on the MBR of your USB stick right now.

So if that is the case, how do I get it to my filesystem? Booting with the stick just brings me to ubuntu.

> **Bashing-om said:**
> googleye; Hi !

To know where grub is installed run these commands from terminal:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub

```and IRT DVD: it is recommended to burn to a cd-r and burn at lowest speed. I have done so many many times, and have yet to experience a problem. (check md5sum).
[INDENT]just try'n to help <==BDQ

[/INDENT]

That shows dev/sda1 which would be ubuntu, the stick is /dev/sdb I think.

---

### Post by googleye on 2012-09-29
Tried to do

```

sudo grub-install /dev/sda1
```

But that just gave me lots of warnings and errors

---

### Post by Bashing-om on 2012-09-29
grub has to be installed onto the MBR of the device ---sda---sda1 is the first partition of the first hard drive. On your grub-install command make it "sda" vice "sda1".
re-run the command as "sda".

Given that the first hard drive is set in your bios boot priority...should boot.

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by googleye on 2012-09-30
I got no errors when installing but upon boot I still get Intel boot agent without the usb stick.. The hard drive is the first to boot.

---

### Post by googleye on 2012-09-30
grub-pc/install_devices: /dev/disk/by-id/usb-Corsair_Voyager_100000059F38CF-0:0

---

### Post by jrog on 2012-09-30
> **googleye said:**
> grub-pc/install_devices: /dev/disk/by-id/usb-Corsair_Voyager_100000059F38CF-0:0
^ That is indicating that GRUB is installing on your USB stick.

---

### Post by googleye on 2012-09-30
Kind of figured that :p weird that installation on sda worked but grub still wasnt there. Anyways I burned the iso and made a fresh install, now i'm working on re-installing everything..

---

### Post by Bashing-om on 2012-09-30
googleye;

grub defaults to installing onto the medium it is installed from or to (hense installing back onto the usb device)
Never having installed from usb ,,I may be out in left field..installing from cd ->..in the final install / confirmation screen is an advanced tab ...the advance tab (non disclosure !) is the advisory where grub is going to be installed. The grub installation point may be changed here at this time.

sure hope this sheds some light on the situation. <==BDQ

---


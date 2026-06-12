---
title: "Command line install using a USB device"
date: 2009-08-22
forum: General Help
---

### Post by m_ad on 2009-08-22
I'm trying to install Ubuntu using the alternate cd installed onto a USB stick. However, when the installation needs to detect the cdrom to install appropriate drivers, it won't detect it (obviously, it's not a cdrom device)

I loaded a virtual console, and found the device on /dev/sdb. When I tried to manually loaded this module, it outputs an error saying invalid module or whatever.

I even mounted the device, /dev/sdb1 to /mnt/somedir and found the contents of the usb stick, so it's the right device.

What can I do?

---

### Post by m_ad on 2009-08-22
Ok, I've tried a few things that don't work. I think I'm close..

During the install, when it fails to detect/mount the cdrom, I say NO to help it detect the module. From there, I switch to the second virtual terminal and mount the usb stick to /cdrom. The contents of the usb stick appear to be on /cdrom. However, during the next stem when it tries to load the components from the CD, it says "There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM. Retry?"

Any ideas?

---

### Post by m_ad on 2009-08-22
It seems that I needed to move the contents of /cdrom/dists/hardy to /cdrom/dists/stable. This worked.

EDIT: another error. Couldn't detect codename for release.

I need a break :lolflag:

---

### Post by ujodarko on 2009-09-03
> **m_ad said:**
> I'm trying to install Ubuntu using the alternate cd installed onto a USB stick. However, when the installation needs to detect the cdrom to install appropriate drivers, it won't detect it (obviously, it's not a cdrom device)

I loaded a virtual console, and found the device on /dev/sdb. When I tried to manually loaded this module, it outputs an error saying invalid module or whatever.

I even mounted the device, /dev/sdb1 to /mnt/somedir and found the contents of the usb stick, so it's the right device.

What can I do?

Hmmm...

I had made LiveCD USB stick with Unetbootin and succeeded to install Ubuntu 9.04 on internal HDD just like that -> in a snap! I've even succeeded to install it to external 2.5" HDD mounted to USB port via that same USB startup disk! Obviously I am lucky guy ;).

No errors, no CDROM issues. Only thing I missed was no chance to choose my language (Croatian) in first step of booting from USB startup stick.

---

### Post by bodhi.zazen on 2009-09-03
He is asking about the alternate CD and not the desktop CD.

I think it is easier to boot the desktop CD (using unetbootin and the desktop .iso) , partition your hard drive with gparted, install with debootstrap (into a chroot) , and then install a kernel, grub, and ubuntu-desktop.

---

### Post by jis on 2009-10-28
> **m_ad said:**
> 
During the install, when it fails to detect/mount the cdrom, I say NO to help it detect the module. From there, I switch to the second virtual terminal and mount the usb stick to /cdrom. The contents of the usb stick appear to be on /cdrom. However, during the next stem when it tries to load the components from the CD, it says "There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM. Retry?"


I have the same problem. I made a bootable USB of Xubuntu 9.10 RC Alternate CD by UNetbootin, but I can't install it to hard drive by the USB media.

---


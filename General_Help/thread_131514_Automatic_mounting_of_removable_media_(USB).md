---
title: "Automatic mounting of removable media (USB)"
date: 2006-02-16
forum: General Help
---

### Post by RichardMatley on 2006-02-16
A brief bit of background:

I've been using various Linux distros for many years, but I'm new to kubuntu (and it's a few years since I last used Debian). I have a laptop which I'm transfering from Gentoo.

I have a number of USB peripherals (flash drives, a hard disk, an ipod etc). The problem is that all of them show up as /dev/sd*, where the * bit varies according to which devices are attached to the machine and in what order. I would like to be able to mount each device (when attached) in a constant mount point.

Under Gentoo I achieved this by using udev so that, eg, the two hard disk partitions were symlinked to /dev/usbhd_freecom1 and /dev/usbhd_freecom2, using a udev entry like this:
> BUS="usb", SYSFS{manufacturer}=="Freecom Technologies", SYSFS{product}=="Classic SL Hard Drive", KERNEL="sd*", NAME="%k", SYMLINK="usbhd_freecom%n"

and making /etc/fstab entries which mounted these at /mnt/usbdisk1 and /mnt/usbdisk2.

Under kubuntu, this is complicated by the fact that these USB devices are automatically mounted as, eg /media/sda1 etc. Also an icon is placed on the desktop which opens those mounts (at first konqueror also opened automatically - I found out that the answer to preventing this was to remove ivman).

What I'd like would be for these devices to be automatically mounted based on my /dev symlinks at mountpoints specified by me, eg /dev/subhd_freecom1 at /media/usbdisk1, rather than at /media/sda1 etc (which depends on the order of connecting devices). If this is not possible I'd like to disable automatic mounting totally.

I have searched the forums, but can't find how to do this. I would appreciate any help people can give. I can't even work out which components/utilities are doing the automounting and placing the desktop icons.

Thanks

---

### Post by xiaoxin on 2006-03-15
applications > system tools > configuration editor

then

Desktop > gnome > volume manager

uncheck automount_media

---


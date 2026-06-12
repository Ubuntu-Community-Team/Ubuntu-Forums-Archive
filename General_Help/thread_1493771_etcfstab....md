---
title: "/etc/fstab..."
date: 2010-05-26
forum: General Help
---

### Post by phillyfandeal on 2010-05-26
Hello all, 

I am trying to get my Dell 720 printer to work in 10.04 and have followed a great instruction guide; however I am now stumped. Here is my /etc/fstab file that it tells me to put in the usbfs which I did; however when I attempt to mount the usbfs its giving me an error.  Any suggestoins?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c05f9a32-3000-4b46-8d08-2b8eb3b9712c /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0


error output is mount: mount point /proc/bus/usb does not exist

Thank you in advance.

---

### Post by anglican on 2010-05-26
> **phillyfandeal said:**
> Hello all, 

I am trying to get my Dell 720 printer to work in 10.04 and have followed a great instruction guide; however I am now stumped. Here is my /etc/fstab file that it tells me to put in the usbfs which I did; however when I attempt to mount the usbfs its giving me an error.  Any suggestoins?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c05f9a32-3000-4b46-8d08-2b8eb3b9712c /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0


error output is mount: mount point /proc/bus/usb does not exist

Thank you in advance.
usbfs is no longer supported by the kernel (not since ~2.6.31-17 IIRC) so quite a few older printers cause problems. There is a workaround, not terribly satisfactory, but usually does the job. The following commands:
```
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
```before printing should do the necessary. After printing it's probably advisable to reverse the above with:
```
sudo umount   /proc/bus
```as you may well break something else.

H

---

### Post by speed32219 on 2010-06-07
Crap, I've been trying to mount the usbfs for the past three hours.  i need to see if the HID drivers has taken over my remote with this fresh install of 2.6.31-22-generic Karmic. 

Dang, i hate updating, now I'll have to install a previous release or try and figure out how to verify that my imon driver is actually loaded of if it is the hid driver. :(

---

### Post by anglican on 2010-06-08
> **speed32219 said:**
> Crap, I've been trying to mount the usbfs for the past three hours.  i need to see if the HID drivers has taken over my remote with this fresh install of 2.6.31-22-generic Karmic. 

Dang, i hate updating, now I'll have to install a previous release or try and figure out how to verify that my imon driver is actually loaded of if it is the hid driver. :(
I suppose it must be possible to compile a bespoke kernel with usbfs included...

H

---


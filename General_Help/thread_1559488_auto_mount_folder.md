---
title: "auto mount folder"
date: 2010-08-23
forum: General Help
---

### Post by LG83 on 2010-08-23
hi,


I use ubuntu 10.04 and I have this folder I don't need that automatically mounts on my desktop.I can remove it with eject, but I would like to know how to prevent its auto-mount, both through the terminal and graphically.

Thanks.

---

### Post by gavinjb on 2010-08-23
Where is the folder located (internal hd, usb flash drive...)

Also can you post your fstab (/etc/fstab)

---

### Post by LG83 on 2010-08-23
I guess it is something I downloaded to my hard disk in windows (I use virtualbox)

here is my fstab:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f0f31901-eb3e-4329-8bab-c53cb2f2cd2c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffbc02b7-7215-4ce1-beed-cf8f5584514f none            swap    sw              0       0

---

### Post by LG83 on 2010-08-23
No ideas? I thought it was an easy one...:roll:

---

### Post by triunenature on 2010-08-23
what exactly are is mounting? is it a usb, an external hdd, dvd drive??

I don't see what i was expecting to see in fstab...

More info please!!!

---

### Post by LG83 on 2010-08-23
This is an iso file that can be located in my winxp under: 
 C:\Program  Files\Oracle\VirtualBox
 
It contains guest additions I downloaded for the virtual box.
On my ubuntu desktop it has the icon of a CD.When checking its properties, it says:
Type: folder (inode/directory).

Hope its clearer now,sorry about any missing details.

---

### Post by gavinjb on 2010-08-24
If it is the Guest Addons then to remove that all you need to do is unmount the CD (under the VirtualBox Devices Menu) and then you should not see it in the future or if not in VirtualBox configure your Ubuntu Virtual Machine and remove the ISO from there.

---


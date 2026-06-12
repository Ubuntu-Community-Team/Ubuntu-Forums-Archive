---
title: "USB Issues with gnome-volume-manager"
date: 2006-04-06
forum: General Help
---

### Post by rowck001 on 2006-04-06
I have both a Laptop and Desktop which both run Breezy.
The laptop is a bit old so I use XFCE4 instead of gnome which runs on the Desktop.

On the laptop I had to manually set up USB mounting/unmounting via /etc/fstab and all works well - when unmounting the usbdisk it unmounts immediately (I used the sync option) performing all its disk writes on-the-fly before unmounting.

However on the desktop, whilst the automounting feature in volume-manager works OK - the disk writes seem to occur on unmounting the usbdisk - taking a long time to perform and some data corruption can occur if the stick is pulled prematurely. Would this indicate that HAL and volume-manager are using async writing which is not optimum for removable media?

Short of disabling gnome removable media automounting and setting up /etc/fstab manually is there any way to see what volume-manager is doing (eg. async or sync writes)??

---

### Post by ranf on 2006-04-07
Plug it in and type mount to see how it is mounted.

---


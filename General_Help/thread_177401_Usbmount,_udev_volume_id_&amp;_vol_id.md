---
title: "Usbmount, udev_volume_id &amp; vol_id"
date: 2006-05-16
forum: General Help
---

### Post by bobslaede on 2006-05-16
Yay, so i installed the ubuntu server, 5.10, with a 2.6.12-9-386 kernel.

I got a problem with usbmount, automounting my usb disks.

Usbmount looks for /sbin/udev_volume_id when i plug in a disk, but that doesnt excist anymore. So i made a symlink from /sbin/vol_id to /sbin/udev_volume_id instead, AFAIK thats what its called now right?

So now usbmount finds the disk, but, wont mount it, 'cause from /var/log/syslog:
 usbmount[21766]: /dev/sda1 does not contain a filesystem or disklabel

Which by far, is not true. It does have a clean Ext3 filesystem, i fsck.ext3'ed it... And on my other ubuntu box i can mount it, i can mount it everywhere, but i want automounting goodness...

So what do i do, to fix this issue? :confused:

---

### Post by Stinger on 2006-05-16
I had some issues too with automounting my usb disks , but since I upgraded my install using the updatemanager ( running kernel 2.6.12-10-386 ) the problem has dissapeared.
BTW I used [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") to add futher repos.

So mabe upgrading would solve your trouble too ?
8)

---

### Post by bobslaede on 2006-05-17
As it turns out, the ubuntu breezy version of udev and usbmount doesnt fit... usbmount is too old.
Installing usbmount 0.0.14 from [http://usbmount.alioth.debian.org/](http://usbmount.alioth.debian.org/) works like a charm

---

### Post by Stinger on 2006-05-17
Strange , I don't have any usbmount installed ?:-k 

Seems like I'm using pmount and hal.
USB works fine here though.:rolleyes:

---

### Post by bobslaede on 2006-05-18
Theres a gnome thing that does all that for you.
I have the Ubuntu Server installed. Without Gnome

---


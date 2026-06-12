---
title: "Where is a usb storage device"
date: 2009-07-23
forum: General Help
---

### Post by tlknv on 2009-07-23
Hi All,
I connected my Sansa Clip MP3 player to the computer's USB port and couldn't find any corresponding storage block device.
GVFS mounts it somehow to ~/.gvfs/<some_nonesence_name> but I want to have an access to the storage device like /dev/sdb. I want to change the label, enable write cache, have an easy and persistent name for the mounted device, etc. It easy to do all of that having an access to the device.
gvfs-mount listed my mounted device as something like gphoto2:/[USB:0,X], where X is a number which always changes. What gphoto2 has to do with non camera usb storage ?
Additional info: Sansa Clip is in MSC mode. I had no problem using my Sansa Clip under Debian Etch and Lenny.
Thanks in advance,
Boris

---

### Post by phillw on 2009-07-23
I'm not familiar with gphoto, but, it is possible in it's infinate wisdom, it is seeing the usb stick as memory for a camera & mounting it. Are there any preferences in gphoto you can check ?

I use F-Spot photo manager, from within 9.04 for 'speaking' to cameras - I guess you use gphoto to support a certain camera.

Hope that helps you in the right direction.

Regards,

Phill.

---

### Post by tlknv on 2009-07-23
I don't know why gvfs associates my usb flash with gphoto2. I don't actually need Ubuntu to mount my usb flash or do something fancy for me. What I need is just plain storage device like /dev/sdb. How can I get it ?

---

### Post by Chronon on 2009-07-23
It sounds like the same issue as here: [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

---

### Post by tlknv on 2009-07-23
Thanks a lot ! I just removed the Sansa Clip entry from /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi and got /dev/sdb.

---


---
title: "possible grub issue"
date: 2011-01-23
forum: General Help
---

### Post by inoh on 2011-01-23
I run Ubuntu on my laptop via USB External HDD.  It always works fine on my laptop.  However if I attempt to boot on any other laptop that supports booting USB Drives it will not boot.  I usually am able to select Ubuntu from GRUB and even see the Ubuntu logo appear, then nothing, just hangs.  If I press ctrl & alt I am sent to shell.  It tells my boot time took too long and usually says could not load root folder, /sbd2 not found.  Any ideas.  I was thinking it could likely be a GRUB issue since you have to redirect the device in order to run Ubuntu off a USB Drive.

---

### Post by dcstar on 2011-01-24
> **inoh said:**
> I run Ubuntu on my laptop via USB External HDD.  It always works fine on my laptop.  However if I attempt to boot on any other laptop that supports booting USB Drives it will not boot.  I usually am able to select Ubuntu from GRUB and even see the Ubuntu logo appear, then nothing, just hangs.  If I press ctrl & alt I am sent to shell.  It tells my boot time took too long and usually says could not load root folder, /sbd2 not found.  Any ideas.  I was thinking it could likely be a GRUB issue since you have to redirect the device in order to run Ubuntu off a USB Drive.

You should not be using **any** /dev/sdx designations in the /etc/fstab file, they should all be UUIDs.

---

### Post by inoh on 2011-01-24
You have to define it as sdx when running off of a External USB source.  Otherwise it boots the first boot, thereafter you are left with the device not loading.  In my case for some reason it only boots from the laptop I used to setup the HDD.  Is it possible I am missing modules to load the External HDD?

---

### Post by inoh on 2011-02-21
here is how I setup the usb hdd

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

note step 11

---


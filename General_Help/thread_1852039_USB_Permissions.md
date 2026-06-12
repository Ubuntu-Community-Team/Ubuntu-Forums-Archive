---
title: "USB Permissions"
date: 2011-09-29
forum: General Help
---

### Post by Paul Baumann on 2011-09-29
&#65279;Acer Netbook with Ubuntu 10.04 Remix Installed.
I can read external HDD, flash drives etc but 
I have lost permissions to write to the USB ports and
eject devices connected.
How do I change permissions to have ownership?
Thanks, Paul

---

### Post by Paul Baumann on 2011-10-10
> **Paul Baumann said:**
> &#65279;Acer Netbook with Ubuntu 10.04 Remix Installed.
I can read external HDD, flash drives etc but 
I have lost permissions to write to the USB ports and
eject devices connected.
How do I change permissions to have ownership?
Thanks, Paul
More clues to my problem:
When I insert a Thumbdrive or External HDD in a USB
port and goto /media and select usb0 I see the data
on the external HDD or Thumbdrive. Viewing Permissions
on usb0 the owner is “root” When I check my other Ubuntu
systems I am the owner and can control file access. 

When I try to unmount the USB device I have the following
message. “unmount: /media/usb0 is not in the fstab (and
you are not root)”
When I try to set up usb0 to share I have the following
message:
(net usershare returned error 255: net usershare add:
cannot share path /media/usb0 as we are restricted to only
share directories we own.
Ask the administrator to add the line “usershare owner 
only = false”
to the [global] section of the smb.conf to allow this.)
Paul

---

### Post by coffeecat on 2011-11-07
@Paul Baumann, I've only just come across this thread with your last post 3 weeks ago. In the hope that you are receiving notifications for posts, I have a suggestion.

> **Paul Baumann said:**
> Viewing Permissions
on usb0 the owner is “root”

...


When I try to unmount the USB device I have the following
message. “unmount: /media/usb0 is not in the fstab (and
you are not root)”

It looks as though you installed the application usbmount. Uninstall it. It is designed for GUI-less systems and interferes with the USB-automounting functionality of the Ubuntu desktop.

---


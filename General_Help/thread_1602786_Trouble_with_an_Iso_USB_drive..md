---
title: "Trouble with an Iso USB drive."
date: 2010-10-21
forum: General Help
---

### Post by Axolotl9250 on 2010-10-21
Hi, I have a USB with a iso disk image written to it for a distro and I'd quite like it erased so I can put another different one on. I was going to to this with UNetbootin. However UNetbootin won't recognise my drive. When I plug it in, it is mounted in /media, and an icon also appears on the desktop. Additionally ```
lsusb
``` returns and entry for it, although ```
fdisk -l
``` does not return anything (these are the things I explored after reading around different pages on USB and mounting. Additionally if I browse the drive and try to just highlight stuff and delete it, it won't work either. The permissions for it are currently ```
dr-xr-xr-x
```, but if I try to change this with chmod to include the w permission, then it just tells me it's a read only filesystem. I'm wondering if I need to be a member of a certain group or somesuch thing, I tried to do su but couldn't (and probably for a good reason too - but I was too used to using su in Arch).

If anyone could help me with this I'd be very grateful,
Cheers,
Ben.

[EDIT]
Solved! Found answers on these pages:
[http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux)
[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/)

---


---
title: "How would I go about installing grub on flash drive to dual boot clonezilla/gparted"
date: 2010-05-15
forum: General Help
---

### Post by josephellengar on 2010-05-15
Yeah, essentially what the title says.  Clonezilla cannot be installed in ubuntu so running a live linux on the usb and installing the applications in that is not an option.  Does anybody have any idea?  Thank you.

---

### Post by john newbuntu on 2010-05-16
One way to do this is by having a multi-boot USB drive wherein you would boot from a USB stick and select the tool/OS that needs to be run.  You should be able to find several examples from Google on how this can be done.

Here's an example that uses grub4dos instead of grub2:  [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

If you are keen on using grub2, look into these example to get an idea on how this can be done:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://clonezilla.org/clonezilla-live/livehd.php](http://clonezilla.org/clonezilla-live/livehd.php)
The grub-install command with the right parameters installs the grub to the USB drive.
You would then copy the .iso files (clonezilla/gparted etc) to a folder on the USB and then 
update your grub.cfg with the appropriate boot commands.

---

### Post by josephellengar on 2010-05-16
> **john newbuntu said:**
> One way to do this is by having a multi-boot USB drive wherein you would boot from a USB stick and select the tool/OS that needs to be run.  You should be able to find several examples from Google on how this can be done.

Here's an example that uses grub4dos instead of grub2:  [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

If you are keen on using grub2, look into these example to get an idea on how this can be done:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
[http://clonezilla.org/clonezilla-live/livehd.php](http://clonezilla.org/clonezilla-live/livehd.php)
The grub-install command with the right parameters installs the grub to the USB drive.
You would then copy the .iso files (clonezilla/gparted etc) to a folder on the USB and then 
update your grub.cfg with the appropriate boot commands.

Thanks!  That's exactly what I needed.  Now I just need to buy a big enough flash drive :P

---


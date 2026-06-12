---
title: "ubuntu on usb created with UNetbootin"
date: 2009-07-15
forum: General Help
---

### Post by darkthunderfx on 2009-07-15
I've never made a bootable OS on a usb drive until today. i made it with UNetbootin, which appears to be what most use. After using it all day and making settings as I wish them to be i realize that the settings/data do not save. i had loaded many programs, but none appear when i reboot. i guess i assumed that when i added files by an installation that they were being written to the usb drive. am i wrong?

how can i make a bootable usb drive of ubuntu that keeps all the the programs/drivers that i add and settings i change?

much thanks!

---

### Post by mano cazalet on 2009-07-16
I guess that unetbootin only creates usb live "cds", that's why your changes were not saves.
You have to make a [persistent install]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/")

---

### Post by darkthunderfx on 2009-07-16
thanks for the response. is this casper-rw the best/most common way of making a persisstant install?

---

### Post by mdurham on 2009-07-16
Assuming that you are using 9.04, there is an entry in the System->Admin menu "Usb startup disc creator" I think this is what you need to use. It uses a program named "usb-creator". Amazing name!
Cheers, Mike

---

### Post by Mighty_Joe on 2009-07-16
> **darkthunderfx said:**
> is this casper-rw the best/most common way of making a persisstant install?

It is the only way to make a persistent install of the Live CD image (the USB Creator mdurham refers to is an automated script of the process posted at PenDriveLinux ).  
I did a full install of Ubuntu to my flash drive. It takes up more room than the Live CD image (2GB vs 750MB), but is much faster because it is not compressed like the Live CD.  
Updating a persistent Live CD USB drive is problematic, as the updates are stored in the persistent partition.  Since there's also a [bug limiting the size of the persistent partition]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544"), it's very possible you'll run out of room.
See my [post here]("http://ubuntuforums.org/showthread.php?t=1193680") if you are interested in a full install.

---

### Post by blazemore on 2009-07-16
The easiest way is already included in Ubuntu!

System -> Administration -> Make USB startup disk

---

### Post by darkthunderfx on 2009-07-16
> **blazemore said:**
> The easiest way is already included in Ubuntu!

System -> Administration -> Make USB startup disk

Looking at what others have said, it appears that a USB startup disk does not allow the user to make changes and have them save to the USB startup disk. ie: when I install aircrack-ng, it does not install/save to the USB drive for later use after I reboot.

---

### Post by blazemore on 2009-07-16
It does, there's an option for persistance built in to the tool.
Unetbootin doesn't have this option.

---

### Post by darkthunderfx on 2009-07-18
> **blazemore said:**
> It does, there's an option for persistance built in to the tool.
Unetbootin doesn't have this option.

Thanks for the response, but I cannot find the option listed. Can you better explain where I must click to find persistence listed in the application window?

---


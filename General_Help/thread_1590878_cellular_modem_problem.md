---
title: "cellular modem problem"
date: 2010-10-08
forum: General Help
---

### Post by TomAbada on 2010-10-08
hi all
i want to use a cellular modem with my ubuntu but it doesnt work from some reason

do i need to install any package or smth ???

---

### Post by searchfgold6789 on 2010-10-08
By cellular modem I am assuming you mean some device that you plug into your USB drive to get internet.
You will probably need to obtain drivers for your model of usb modem from the internet.
[RIGHT][SIZE=1]...Which might not be possible because your internet is what you are trying to fix...[/SIZE]
[/RIGHT]

---

### Post by efflandt on 2010-10-08
It may be impossible for someone to come up with a relevant answer when you have not even mentioned specifically what type of device you are trying to use or cellular provider. Some might initially come up as a usb mass-storage device if drivers are on the device itself.

You might at least post the output of **lsusb** and point out which device it is, or the part of **sudo lsusb -v** specific to that device (assuming it is a USB device).

---


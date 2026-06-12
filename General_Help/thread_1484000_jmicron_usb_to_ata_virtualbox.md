---
title: "jmicron usb to ata virtualbox"
date: 2010-05-15
forum: General Help
---

### Post by thebigob on 2010-05-15
Hi hopefully someone can help.

I have installed virtualbox on Lucid (the one from suns website)

This sees my freecom usb hard disk dock as a jmicron usb to ata device.

This seems ok. 

The problem is when I run virtualbox with this plugged in it is greyed out and says no usb devices attached...

I have added my user to the vboxusers group. I have also tried unplugging and plugging in one the virtualbox is running nothing seems to get the device discovered although ubuntu mounts it straight away. Perhaps this is the issue?

I am happy to provide screenshots and more info if required.

Appreciate any pointers.

Cheers

---

### Post by thebigob on 2010-05-16
Ok I got this working by reading the manual :P

Solution was to create a usb group and add myself to it.

Once this was done I added:

none     /proc/bus/usb     usbfs      devgid=1001,devmode=664    0    0

to /etc/fstab

where 1001 is the id of the group you created.

Once this was done all was well.

Hope this helps someone else.

---


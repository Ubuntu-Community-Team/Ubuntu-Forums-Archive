---
title: "Strange behavior when mounting usb pendrives"
date: 2010-10-12
forum: General Help
---

### Post by foxvan on 2010-10-12
Today i have plugged a usb pendrive which usually mounted without any problem. Right now I have these issues:

[LIST]
[*]Just the super user can umount it.
[*]I cannot make any modification to the content inside without being a super user.
[*]Several usb0, usb1, usb2, ... folders, appear in my /media folder, but i don't know since when.
[*]On the Places menu appear two entries for each usb mounted device (don't know if booting the system with the devices plugged in will work).
[/LIST]
I plugged a usb pendrive and two devices appeared, GISCIENCE and usb1, i just can access the pendrive itself through usb1 but not from GISCIENCE which actually is the name of the pendrive. In this point there is just one mount point:

/dev/sdc1 on /media/usb1
 
In nautilus there was still the link to GISCIENCE, so I made click and it mounted and begin working as usually (no permission problems).

Any idea?

---

### Post by foxvan on 2010-10-13
I have been googling with other keywords nad i have found my problem in other thread:

[http://ubuntuforums.org/showthread.php?t=1478368&page=4](http://ubuntuforums.org/showthread.php?t=1478368&page=4)

The problem was the package usbmount which is a dependency of pmount. I do not know when was it installed, but well it worked for me.

What i did in concrete was this:

sudo apt-get remove usbmount
sudo apt-get autoremove

With the last command pmount was deleted from my system.

---


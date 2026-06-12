---
title: "Burn ISO while running live xubuntu?"
date: 2010-01-28
forum: General Help
---

### Post by JesterDev on 2010-01-28
I am running a live version of xubuntu (8.10) (no OS installed) and I want to burn an ISO (Ubuntu 9.10). How can I do it?  

I cannot eject the CD, and have no other drives (laptop). 

I don't want to install xubuntu, then burn.

Drive will not unmount error: "device is not in /media/.hal-mtab so it is not mounted by HAL"

---

### Post by snowpine on 2010-01-28
Impossible without two CD drives. :)

Do you have a USB thumb drive you can use for the purpose?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sisco311 on 2010-01-28
Or you can create a 750MB~2GB partition & use it to install ubuntu. After the installation you can reformat it as a swap partition.

[uhelp]community/Installation/FromLinux[/uhelp]
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by gradinaruvasile on 2010-01-28
Well if you have an usb stick you can use the Ubuntu's usb creator to write your iso to the stick - it also makes it bootable. Its a better way to install Ubuntu because its way faster than the cd.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

From 8.10 you should have the usb creator under the administration menu. And your laptop should be able to boot from usb (all newer ones can
).

---

### Post by blueshiftoverwatch on 2010-01-28
> **snowpine said:**
> Impossible without two CD drives. :)
This probably wouldn't work and I'm too lazy to try it out myself and find out. But what if you loaded up Xubuntu, started the CD burning application, manually ejected the live CD (pushing a pin into the manual eject button on your CD drive), and put a blank CD in? Theoretically all of the information required to burn the CD would already be loaded into the RAM and the blank CD would be recognized.

---

### Post by gradinaruvasile on 2010-01-29
Probably your system would just lock up. But who knows...

---


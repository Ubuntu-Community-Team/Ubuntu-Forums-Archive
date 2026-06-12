---
title: "update from 11.4 to 11.10 = lost dual boot  Help"
date: 2011-11-23
forum: General Help
---

### Post by AlexBill on 2011-11-23
Hi all
I have a laptop (amilo pentium M) with Win XP and Ubuntu 11.4. When I trurn on computer there is a menu to choose between both OSs, every thing was fine.
Yesterday i burned the 11.10 ISO in a CD and installed it. Installation was successfully. When I reboot computer it just shos a promt like
grub rescue>_

I started ubuntu 11.10 in CD live mode, and i did this:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
After reboot, at least i can login on Windows but ubuntu i cant.

I also burned a CD with Rescatux and boot with it and when i run grub install it says:
"Grub was not installed. Something went wrong" :(

I also tryed grub4dos. it works fine for booting windows but when I choose grub4dos boot it says:

Booting grub2
find --set-root /boot/grub/core.img
(and nothing more is shown)

Please, can you help me recover the beautifill menu I used to have in order to boot any of the OSs?

Thanks a lot
Alex Bill

---

### Post by zvacet on 2011-11-23
Try to reinstall grub following [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by AlexBill on 2011-11-23
> **zvacet said:**
> Try to reinstall grub following [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I did that, it was installed successfully but after reboot I saw this error:
error: no such partition
grub rescue_

:-(

Alex Bill

---


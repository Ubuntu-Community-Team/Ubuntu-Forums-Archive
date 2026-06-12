---
title: "SD card issue on Ubuntu Netbook Remix 9.10 on EEE PC 1000HE"
date: 2010-01-24
forum: General Help
---

### Post by ryu kun on 2010-01-24
Hi!

My Ubuntu Netbook Remix 9.10 on my Asus EEE PC 1000HE computer does not recognize SD card.

"sudo fdisk -l" command does not result anything related to SD card even when the card is in the slot.

Last line of of the /etc/fstab file is:

> /dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Please help...

---

### Post by ryu kun on 2010-01-25
I've managed to use SD card slot by using eee-control. Its website is [here]("http://greg.geekmind.org/eee-control/"). Package for Karmic can be found [here]("http://danamlund.dk/eee-control/eee-control.html").

---


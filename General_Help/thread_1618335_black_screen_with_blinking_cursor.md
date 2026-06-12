---
title: "black screen with blinking cursor"
date: 2010-11-10
forum: General Help
---

### Post by frankbooth on 2010-11-10
Just did a fresh Ubuntu 10.10 **(minimal) **install on my Asus EEE PC 1001PX.
Before the minimal install I had Ubuntu Netbook Edition 10.10 which worked flawlessly, now all I get is a black screen with a blinking cursor:

[IMG]http://data.fuskbugg.se/dipdip/2010-11-10-194510.jpg[/IMG]
[SIZE=1]Sorry for the amazing quality, but I guess it's better than nothing.[/SIZE]

ctrl+alt+Fx does nothing, ctrl+alt+del reboots the computer.

[B]Booting with the usb-stick that was used for the install takes me to the login... what the hell?
Any idea what's going on?[/B]

---

### Post by blueridgedog on 2010-11-10
Try nomodeset, see the link in my signature.

---

### Post by frankbooth on 2010-11-10
Can't enter grub (holding SHIFT during boot), I tried it out by editing /etc/default/grub (since I can boot with the usb for some reason) but it didn't work. 

It's as if something I need to boot is saved on the usb stick, I mean...
Booting the usb should take me to the install of Ubuntu, but it boots my system instead.

---

### Post by frankbooth on 2010-11-12
**Solved.**

When doing a minimal install of ubuntu from a usb it seems to install grub on the usb by default.

[B]How-to:
[/B]
**1)** After installation boot from the usb again (since you have no grub on the hdd, you need the usb for now)

**2)** ```
df
```
output will be something similar to:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            150814948   1840152 141313844   2% /

```

**3)** ```
sudo grub-install /dev/sda
sudo update-grub
sudo reboot
```

**4)** You can now boot from the hdd like normal

---


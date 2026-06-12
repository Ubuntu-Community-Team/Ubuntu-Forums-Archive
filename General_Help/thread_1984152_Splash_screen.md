---
title: "Splash screen"
date: 2012-05-21
forum: General Help
---

### Post by kurci2 on 2012-05-21
Hi!
I have installed Ubuntu 12.04 32-bit with encrypted lvm via alternate CD.
After install i got "no video mode activated" error, but i fiked it with this workaround:
```
cd /usr/share/grub/
sudo cp *.pf2 /boot/grub/
sudo update-grub
```
now this error is gone, but there is another problem...

When i boot my laptop i see this (see attached picture: 21052012227.jpg) screen instead of nice splash screen...

After i press escape twice it looks as it should.

Does anyone know what should i do, or is it a known bug with no fix published yet??

---


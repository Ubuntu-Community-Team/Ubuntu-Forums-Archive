---
title: "Writing udev rule for ZEN"
date: 2009-11-24
forum: General Help
---

### Post by Jordanwb on 2009-11-24
Since mtpfs is the only thing my ZEN will work with and I don't feel like typing "sudo mtpfs -o ..." everytime, I've trying to write a udev rule for it.

This is what I have in /etc/udev/rules.d/45-mtpfs.rules:

```
ATTR{idVendor}=="041e", ATTR{idProduct}=="4157", SYMLINK+="mtpfs -o allow_other /media/mp3", MODE="660", GROUP="audio"
```

I checked lsusb -v for idVendor and idProduct and they are correct, but gphoto2 keeps mounting my ZEN.

---


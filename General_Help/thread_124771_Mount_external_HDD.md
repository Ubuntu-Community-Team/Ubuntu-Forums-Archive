---
title: "Mount external HDD"
date: 2006-02-02
forum: General Help
---

### Post by hove99 on 2006-02-02
Hi :-)

I want to mount an external USB ext3 formatted HDD in a fixed folder/mount point, so that every time I connect the HDD, it mounts e.g. in the folder /media/hdd. I remember seing a HOWTO, but now I cant find it. Anyone know the link/how to do?

Thanks :-)

---

### Post by lamego on 2006-02-02
I am not sure if this works for plugable devices:

Plug the disk and check what is the device name, just type "mount".
Now edit the file system table:
```
sudo gedit /etc/fstab
```
Just add an entry to the usb device.

---


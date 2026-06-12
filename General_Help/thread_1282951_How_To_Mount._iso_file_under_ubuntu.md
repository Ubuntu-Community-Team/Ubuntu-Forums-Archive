---
title: "How To Mount. iso file under ubuntu"
date: 2009-10-05
forum: General Help
---

### Post by BAMF1501 on 2009-10-05
Yes i have a 5.44gb file .iso format its a game an di want to moun the disk image to install the game how do i do so ??

---

### Post by anonymous_user on 2009-10-05
[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

---

### Post by FakeOutdoorsman on 2009-10-05
A simple terminal command works too.  First, make a directory:
```
mkdir mountediso
```
Now mount the ISO:
```
sudo mount ubuntukarmic.iso mountediso -o loop
```
To unmount:
```
sudo umount mountediso
```

---


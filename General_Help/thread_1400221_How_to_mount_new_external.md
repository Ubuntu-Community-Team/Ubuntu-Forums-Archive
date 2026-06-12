---
title: "How to mount new external"
date: 2010-02-06
forum: General Help
---

### Post by johnnysnotdead on 2010-02-06
Hello,

Just bought a new external and usually i would be able to mount things but i cannot log into GDM so im suck doing it in the terminal like thing. 

so far i have tried:

```
sudo fdisk -l /dev/sdb
```

```
sudo mkdir /media/usbdrive
sudo mount -t msdos /dev/sdb1 /media/usbdrive
```

but when i do that is says 

```
FAT: bogus num of reserved sectors
mount: wrong fs type, bad option, bad superblock on /dev/sdb1
```

any suggestions?

comp: Dell Inspiron E1505
OS: 9.10
HD: Segate Free Agent Go 320GB

---

### Post by johnnysnotdead on 2010-02-06
```
sudo mount -t ntfs /media/exhd /dev/sdb1
```

that worked

found it here just in case you have the same problem

[http://ubuntuforums.org/showthread.php?t=1392147&highlight=mount+external+terminal&page=2](http://ubuntuforums.org/showthread.php?t=1392147&highlight=mount+external+terminal&page=2)

---


---
title: "mkfs and automount"
date: 2010-11-05
forum: General Help
---

### Post by brubizu on 2010-11-05
Hi, everytime a use the mkfs as soon as it finishes, ubuntu mounts it and open the device on nautilus, i don't want that, I want it to make the filesystem and leave it unmounted, or at least unmount it asap, i tried unchecking the automount in gconf-editor, but got no resuls... anyone knows how to do it?

i also tried :
```
mkfs.ext3 -L casper-rw /dev/sda3 && umount /dev/sda3
```but that didn't work because it tries to unmount before it is mounted, I know I could use

```
mkfs.ext3 -L casper-rw /dev/sda3 && sleep 4 && umount  /dev/sda3
```but that just seems like an awful solution....

---


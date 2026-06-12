---
title: "how to install windows, after creating a image disk with qemu-img?"
date: 2009-10-17
forum: General Help
---

### Post by frenchn00b on 2009-10-17
how to install windows, after creating a image disk with qemu-img?

the drive C remains unfound :(

---

### Post by frenchn00b on 2009-10-17
> **frenchn00b said:**
> how to install windows, after creating a image disk with qemu-img?

the drive C remains unfound :(

solved

very important. get a bootable disk.
here there is one
(post me if you would like one)

1- create teh disk
qemu-img create testdisk.img 2000M

2-type:
qemu -fda WINDOWSSEIMA.ima -hda testdisk.img -boot a -localtime -soundhw sb16 -no-kqemu -cdrom mywindowsinstallcdrom.iso 

3-
fdisk
press enter enter yes. ... straightforward

4-restart
(alt ctrl)

5-format c:
6-eventluylly restart
6- r:
isntall windows

---

### Post by cabrey on 2009-10-17
How does this relate to Ubuntu?

---

### Post by frenchn00b on 2009-10-17
> **cabrey said:**
> How does this relate to Ubuntu?

qemu is available under windows and linux, ubuntu. so far so good, all is working. Best regards

---


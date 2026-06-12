---
title: "HDD added not appearing"
date: 2006-02-06
forum: General Help
---

### Post by ttallos on 2006-02-06
I have added a slave hard drive to my ubuntu machine, it does not appear the drive is fat32 when I try to mount it(typing /dev/hdb or mount/hdb)... I just get errors saying no such drive present??? Any ideas out there??

---

### Post by Sutekh on 2006-02-06
Well what is the output of fdisk when you type this in a terminal?
```
sudo fdisk -l
```
The partition will probably be hdb**1** not simply hdb, but fdisk will confirm or not.

---

### Post by ttallos on 2006-02-06
Thats good info for later I am reloading just now but I think I just typed hda hdb hdc looking for it I know that way isn't as good now. the hdb1 thing makes sence.

---


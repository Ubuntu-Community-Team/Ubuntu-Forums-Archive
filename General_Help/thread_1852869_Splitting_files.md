---
title: "Splitting files"
date: 2011-10-01
forum: General Help
---

### Post by Condor Cluster on 2011-10-01
I have a 4.2 Gb ISO on one ubuntu netbook, that I want to transfer and burn on another ubuntu laptop.

I do have an external drive, formatted in FAT 32, which would not let me copy the whole ISO file onto it :(

Could some please tell me the command that would say, split the ISO into 2 x 2 Gb files, and then the command to join then back again at the other end?

Much appreciated :p

---

### Post by demonipuch on 2011-10-01
Hello

You can use the split command :
```
split -db 2147483648 image.iso image
```In order to merge the splited files : 
```
cat image00 image01 image02 > image.iso
```

---

### Post by Condor Cluster on 2011-10-01
Thanks, just what I was looking for!

:D

---


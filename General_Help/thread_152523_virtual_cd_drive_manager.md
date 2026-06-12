---
title: "virtual cd drive manager"
date: 2006-03-30
forum: General Help
---

### Post by RajivNair on 2006-03-30
is there any virtual cd manager for ubuntu,like alcohol120%??

---

### Post by gord on 2006-03-30
you can either convert your cd's to .iso with:
```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024
```
and mount them with:
```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

or use [cdemu](http://cdemu.sourceforge.net/), which can mount cue/bin files.

---

### Post by hw-tph on 2006-03-30
To mount Goldenhawk type CD images (.bin/.cue file sets) you will need to use [cdemu](http://cdemu.sourceforge.net/).


Håkan

---

### Post by RajivNair on 2006-03-30
thanks

---

### Post by adamkane on 2006-03-31
Nautilus:
[http://www.ubuntuforums.org/showthread.php?t=149963](http://www.ubuntuforums.org/showthread.php?t=149963)

Konqueror:
[http://www.ubuntuforums.org/showthread.php?t=144236](http://www.ubuntuforums.org/showthread.php?t=144236)

---


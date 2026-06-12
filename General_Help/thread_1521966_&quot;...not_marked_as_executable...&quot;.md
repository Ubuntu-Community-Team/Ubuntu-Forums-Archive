---
title: "&quot;...not marked as executable...&quot;"
date: 2010-07-01
forum: General Help
---

### Post by Muskiet on 2010-07-01
I run Ubuntu 10.04 LTS and I'm trying to run a Windows program under Wine from a CD.
I get the normal "...not marked as executable..." message when trying to start the Setup.exe file but when trying to change its permission to "allow executing file as program" I get a message that this is not possible because of the read-only file system.

Therefore my question:
How do I run a windows setup file from a CD without having to change the permission?

---

### Post by TeoBigusGeekus on 2010-07-01
You could create an iso image of the cd and then mount it on your hard disk.

---

### Post by lalitpur on 2010-07-16
Try this.   It is a little longer than necessary, but might be more easily understood:

Insert the CD
```
mount -l
```
(lists existing mount point of CD)
```
sudo umount /media/diskname
```
(or name of mounted disk listed above)
```
sudo mkdir /media/mycd
```
```
sudo mount -t iso9660 -o mode=0777,exec /dev/sr0 /media/mycd
```
(/dev/sr0 is also from mount command above)

Hope this helps.

---


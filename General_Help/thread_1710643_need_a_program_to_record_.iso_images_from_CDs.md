---
title: "need a program to record .iso images from CDs"
date: 2011-03-20
forum: General Help
---

### Post by rockager on 2011-03-20
is there any linux program which can  record .iso images from CDs?
if there is can someone please give me the download link or the package name (if it's in the repositories).

i would also like to know if it's against the forum rules to start a duplicate thread in a different support category as my thread in the hardware&laptops support category has not been answered.
[http://ubuntuforums.org/showthread.php?p=10579623](http://ubuntuforums.org/showthread.php?p=10579623)

---

### Post by spiky001 on 2011-03-20
What are you trying to do with the iso,s maybe a little more info might help

---

### Post by timgood on 2011-03-20
Insert the CD or DVD into your drive. Open a terminal and type:

```
 cat /dev/sr0 > /home/<yourname>/<filename>.iso
```

Where /dev/sr0 is the device name for your drive. You can find this by inserting a data disk in your drive and then opening System Monitor and looking at the 'File Systems' tab. Obviously replace <yourname> with your login name and <filename> with an appropriate choice.

The image file can be mounted and checked using disk mounter.

---

### Post by Quackers on 2011-03-20
Brasero > copy disc > set as .iso

---

### Post by Quackers on 2011-03-20
See post #4 for a better explanation (if the cd you want to copy is a .iso image)
[http://ubuntuforums.org/showthread.php?t=1700375](http://ubuntuforums.org/showthread.php?t=1700375)

---

### Post by rockager on 2011-03-21
thanks everyone!

---


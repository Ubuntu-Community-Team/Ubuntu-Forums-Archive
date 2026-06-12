---
title: "How to format external HHD ?"
date: 2011-08-05
forum: General Help
---

### Post by mrpenguin on 2011-08-05
I have an external Hard drive I wish to format through my Laptop that is running Ubuntu 10.04
The external HHD already have Ubuntu on it but I need to format it to work on a windows 7 computer.
Windows 7 dont see the HHD when I have it connected.

When I connect it to my Ubuntu Laptop and try and format it to NTFS I keep getting an error saying it cant format because the drive is busy.

Any Ideas ? thanks.

---

### Post by ruffEdgz on 2011-08-05
WARNING - This process will erase everything on the external hard drive. Please proceed at your own risk.

I would recommend installing a program called 'gparted' which should handle your request
```

sudo apt-get install gparted

```
Once installed, you should be able to start up the application, find the external hard drive you want to format to NTFS. I would recommend looking over this help doc found on their website to learn more:

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

Cheers!

---

### Post by oldos2er on 2011-08-05
> **mrpenguin said:**
> When I connect it to my Ubuntu Laptop and try and format it to NTFS I keep getting an error saying it cant format because the drive is busy.

Make sure the drive is unmounted before formatting it.

---

### Post by mrpenguin on 2011-08-10
Thank you

---

### Post by Ad1217 on 2011-08-10
Someone already said, but make sure to back up first!! you will lose everything!!! (as in ubuntu on the external hard drive)

---


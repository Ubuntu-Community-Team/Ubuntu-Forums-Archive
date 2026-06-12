---
title: "Windows 7 on flash drive"
date: 2010-11-05
forum: General Help
---

### Post by luposolo on 2010-11-05
How would I install windows 7 on a flash driveon ubuntu. I know how to do it through windows. There was this really user friendly piece of software that would do it all for you. Is there something like that on ubuntu?

---

### Post by JustinR on 2010-11-05
According to this:
[http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/](http://www.addictivetips.com/windows-tips/install-windows-7-from-usb-drive-requires-2-simple-steps/)

All you need is to have the Windows Disk .ISO file and at least a 4GB flash drive and some software:

Go to Applications > Accessories > Terminal: and type
```

sudo apt-get install unetbootin

```

Everything else from there should be self-explanatory but if you need help just ask us!

Good Luck!

---

### Post by wilee-nilee on 2010-11-05
> **luposolo said:**
> How would I **install** windows 7 on a flash driveon ubuntu. I know how to do it through windows. There was this really user friendly piece of software that would do it all for you. Is there something like that on ubuntu?

Install or load the ISO for installation?

---

### Post by luposolo on 2010-11-05
I am trying to put windows 7 ISO image on my usb flash drive and to install it through my usb flash drive. I haven't found any information on how to do it on ubuntu. all the information is all on windows do I have any hope. I want to install windows so I can play bloodline champions. If anyone helps me fix my problem I will see if I can invite you into the beta. also I prepared the drive for Unetbootin but it doesn't even reconize my usb flash drive

---

### Post by wilee-nilee on 2010-11-06
So I just did a successful loading of a thumb in Maverick, booted up with no problems.

I formatted the thumb to ntfs, I put the bootflag on it. I then just extracted the Legit W7 ISO I got from Digital River to the thumb by right clicking the ISO and using archive manager to extract to the thumb.

This extraction builds the same files on the thumb as I have on my other thumb loaded with the W7 loader from MS.

---


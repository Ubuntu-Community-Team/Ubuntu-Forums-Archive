---
title: "Format &amp; Partition Software"
date: 2010-12-12
forum: General Help
---

### Post by vchapman on 2010-12-12
I think that the hard disk in one of my computers got hit with a power spike. Anyway the system no longer boots. I tried to reinstall Ubluntu 10.04, but it can't be written to the disk. 

So, at one point I had a cd with software that would allow me to format and partition a disk as a separate operation. If someone could point me to a site where I could obtain that software, it will be appreciated. TIA

---

### Post by argedion on 2010-12-12
use gparted on the live cd if for some reason its not there you can get a live gparted from:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I would try to check the disk first to see if its toast. if it is then the only thing you can do is replace it. gparted is a great tool to have but it wont work if the drive has physical damage to it. You may want to try getting a program from the disk manufacture that can test the disk and tell you if there is any damage

---

### Post by tajiknomi on 2010-12-12
> **vchapman said:**
> I think that the hard disk in one of my computers got hit with a power spike. Anyway the system no longer boots. I tried to reinstall Ubluntu 10.04, but it can't be written to the disk. 

So, at one point I had a cd with software that would allow me to format and partition a disk as a separate operation. If someone could point me to a site where I could obtain that software, it will be appreciated. TIA

[SIZE=2]In My opinion Gparted is one suitable for partitioning, you can Run it from Ubuntu live-CD or you can download Gparted live-Cd and can burn on disk or Usb[/SIZE] > [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Gparted Live > [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by karthick87 on 2010-12-12
If it is not there,you can install it
```

sudo apt-get install gparted
```

---


---
title: "Boot Repair Hangs"
date: 2012-08-03
forum: General Help
---

### Post by jim_deadlock on 2012-08-03
My disks look like this:

SDA (120Gb SSD) - sda1 (/) sda2 (swap)
SDB (2Tb HDD) - sdb1 (grub) sdb2 (/home)
SDC (80Gb HDD) - encrypted
SDD (400Gb HDD) - sdd1 (storage)

My aim is to move grub from SDB to SDA.

I tried booting from a normal live CD, installed boot-repair and ran it. The scanning dialog appeared:

```
Scanning systems. This may require several minutes...
```

and the progress bar moved back and forth like it was doing something. I left it for over 30 mins like that but nothing more happened and I eventually aborted.

Next I burned a Boot Repair live CD (at minimum speed) and ran it. During startup the following message appears about 10 times:

```
Buffer I/O Error on device sr0
```

... but after that it seems fine, the GUI comes up and then I activate it and the Scanning dialog appears like before. Again it stays there for 30+ mins until I abort.

So is this a problem with one of my disks not being recognised (they all function normally in daily use)? Any suggestions for an alternative method of transferring my grub partition?

---

### Post by dcstar on 2012-08-04
> **jim_deadlock said:**
> 
........
Any suggestions for an alternative method of transferring my grub partition?

Boot normally, then:

```
sudo dpkg-reconfigure grub-pc
```

Select the different drive to install the Grub bootloader. Change the BIOS to boot off the different drive.

---

### Post by jim_deadlock on 2012-08-04
Perfect! Thanks!

---


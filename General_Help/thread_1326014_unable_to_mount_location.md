---
title: "unable to mount location"
date: 2009-11-14
forum: General Help
---

### Post by majoob on 2009-11-14
n00be question:
I just purchased a usb HD dock + internal HD for backups.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817155014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817155014)
and a Seagate SATA internal HD.

I can't get it to mount. It shows up in Places > Computer > USB Drive with the orange usb emblem but it will not mount. Gives me an "Unable to mount location" error.

It probably needs to be formatted first, but how?

---

### Post by majoob on 2009-11-14
Anyone?

---

### Post by majoob on 2009-11-16
Its been 2 days so I'm going to bump this.
Can anyone help me?

---

### Post by dread22 on 2009-11-16
nice graphical way of doing it is opening gparted and formatting from there.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Is it the internal or the dock that wont mount?

---

### Post by majoob on 2009-11-16
> **Sin@Sin-Sacrifice said:**
> Is it the internal or the dock that wont mount?

I'm not sure. Is there a way to determine that? The drive is SATA, so I suppose I could connect it as a second internal drive.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Ok... the dock. I was a little confused. I thought you had 2 drives... one internal and one in the dock. Sorry... what comes of running ```
fdisk -l
``` in the terminal?

---

### Post by majoob on 2009-11-16
I believe sdb is the new internal drive + usb dock. sda is my internal drive, which is identical. See the last line below: 

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120378   966936253+  83  Linux
/dev/sda2          120379      121601     9823747+   5  Extended
/dev/sda5          120379      121601     9823716   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
This ```
Disk /dev/sdb doesn't contain a valid partition table
``` is why it wont mount. Open gparted... System>Admin>Gparted or it might say partition editor. Top right should show /dev/sda in the button. Click it and change over to /dev/sdb and reformat it in your fav filesystem then try to mount it.

---

### Post by majoob on 2009-11-17
> **Sin@Sin-Sacrifice said:**
> This ```
Disk /dev/sdb doesn't contain a valid partition table
``` is why it wont mount. Open gparted... System>Admin>Gparted or it might say partition editor. Top right should show /dev/sda in the button. Click it and change over to /dev/sdb and reformat it in your fav filesystem then try to mount it.

Cool, thanks. I installed GParted and the top right dropdown lets me switch to sdb (my usb docked internal).

So, what filesystem should I format it to? My primary HD is ext3. I run Ubuntu nearly exclusively but occasionally run XP in a virtual machine.

When I click on Device > Create Partition Table (or Partition > New) in GParted it gives me these options in Advanced: msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun and loop.

---


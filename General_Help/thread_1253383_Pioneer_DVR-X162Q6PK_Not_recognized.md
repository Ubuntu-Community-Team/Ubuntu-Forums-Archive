---
title: "Pioneer DVR-X162Q6PK Not recognized?"
date: 2009-08-30
forum: General Help
---

### Post by ogwilson on 2009-08-30
I'm needing to burn a disc using my external dvd burner (i do not have an internal drive) and Ubuntu doesn't recognize it. I am just wondering how I can get it to work in Ubuntu? I really need to burn several files, archives, and ISOs. Thanks and any help incoming is greatly appreciated

[http://www.bestbuy.com/site/olspage.jsp?skuId=9254175&st=pioneer+dvd+burner&lp=4&type=product&cp=1&id=1218069254016](http://www.bestbuy.com/site/olspage.jsp?skuId=9254175&st=pioneer+dvd+burner&lp=4&type=product&cp=1&id=1218069254016)

---

### Post by Bucky Ball on 2009-08-30
Have you tried plugging it in and putting a CD/DVD in? What happens?

---

### Post by ogwilson on 2009-08-30
Yes, plugging it in and trying to put media in is what alerted me to the problem. Looked in the Computer folder, it wasn't recognized there. Here's a look at my fstab

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b16adedb-2440-44bf-bc62-59217d32fd2c /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# swap was on /dev/sda5 during installation
UUID=fc82207b-7ef3-452e-8460-dbec3665bf89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by ogwilson on 2009-08-30
Also it may be worthy to note that I installed the OS using this very external DVD drive, so im not sure why it wouldn't be able to recognize it. Here is the product in question on Best Buy:

[http://www.bestbuy.com/site/olspage.jsp?skuId=9254175&st=pioneer+dvd+burner&lp=4&type=product&cp=1&id=1218069254016](http://www.bestbuy.com/site/olspage.jsp?skuId=9254175&st=pioneer+dvd+burner&lp=4&type=product&cp=1&id=1218069254016)

I should also note that I am on 9.04.

---

### Post by Bucky Ball on 2009-08-30
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```That's probably it, unless you have another in the box. Could you post the result of:

```
sudo blkid
```with the device plugged in and switched on, please?

Is it usb? Try:

```
lsusb
```in a terminal with it plugged in, switched on.

Also, with it in and on:

```
sudo mount -a
```

That will attempt to mount anything plugged in or otherwise!

---

### Post by ogwilson on 2009-08-30
I'm sorry, it seems I'm a bit of an idiot. There was a USB cable hooked up to the port where I usually have my DVD drive, it just so happens that that USB cable wasn't the one hooked up to my external, lol. Sorry for wasting your time, I'll be more attentive next time. Thanks for attempting to help either way!

---

### Post by Bucky Ball on 2009-08-30
Hahaha! lol. Hey, these things happen! Happy burning.

---


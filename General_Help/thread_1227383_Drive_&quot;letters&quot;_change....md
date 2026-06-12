---
title: "Drive &quot;letters&quot; change..."
date: 2009-07-30
forum: General Help
---

### Post by bla4free on 2009-07-30
I have all SATA drives in my 8.04 system. When I installed it, it installed to /dev/sda. After hooking up some external SATA drives, my boot drive is now /dev/sdd. Why would these letters change? And in my fstab, it still shows it as sda:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8cefe393-de84-4876-9037-ce1e61f292ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f52f0782-3ef0-4704-a9ba-da45f3c62289 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Why would this change?

---

### Post by itsamebuddich on 2009-07-30
Bing "udev", that should solve your problems here.

---

### Post by bla4free on 2009-07-30
> **itsamebuddich said:**
> Bing "udev", that should solve your problems here.

What does that mean?

---

### Post by michy99 on 2009-07-30
Instead of using the /dev/ designations for your partitions, you should use the UUID as these do not change. To find the UUIDs of your drives, use```
blkid
```Replace the /dev/sda1 type designation in fstab with UUID=whatever_the _UUID_is.

EDIT: Never mind, I just looked at your fstab again, and it already uses the UUID. The comment above it just tells you where it was when you first installed Ubuntu. You can change it if you want. It is ignored by the computer anyway.

---

### Post by bla4free on 2009-07-30
Is there a way I could give the partitions a "label" per se so I wouldn't need the UUID?

---

### Post by scouser73 on 2009-07-30
Use this method to [[COLOR="Red"]**Rename A Hard Drive**[/COLOR]]("https://help.ubuntu.com/community/RenameUSBDrive").

---

### Post by michy99 on 2009-07-30
You can label partitions with tune2fs. I think gparted can do it also.

---

### Post by capscrew on 2009-07-30
> **bla4free said:**
> I have all SATA drives in my 8.04 system. When I installed it, it installed to /dev/sda. After hooking up some external SATA drives, my boot drive is now /dev/sdd. Why would these letters change? And in my fstab, it still shows it as sda:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8cefe393-de84-4876-9037-ce1e61f292ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f52f0782-3ef0-4704-a9ba-da45f3c62289 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Why would this change?

Linux applies /dev/sd***xn***in the order it discovers the devices.  The UUID stays the same.  Your external devices are being discovered before the boot partition.  This is normal behavior.  Your /etc/fstab is using the UUID to ID the partition.  The *# /dev/sda1* is just a comment.  See here:```
# /dev/sda1 [COLOR="Red"]<--- comment only[/COLOR]
UUID=8cefe393-de84-4876-9037-ce1e61f292ec /               ext3    relatime,errors=remount-ro 0       1
```

EDIT: You can always add to the comment in /etc/fstab i.e. # /dev/sda1 [COLOR="DarkSlateGray"]-- boot partition[/COLOR]

---


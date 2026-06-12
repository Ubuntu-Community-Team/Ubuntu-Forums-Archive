---
title: "How to delay mount an ext USB drive"
date: 2010-11-29
forum: General Help
---

### Post by meazz1 on 2010-11-29
I have an usb external hd I need to delay mount. If I enter the information in the /etc/fstab, on a reboot I get an error that the drive is not ready.
If I manually mount it, it works fine. problem only occurs after a reboot or restart.

I need to mount it automatically after I have logged in. I am not sure how to go about doing this.

this is the out put of the fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001   83  Linux

this is the /etc/fstab entry
UUID=a52b06f6-9453-42ce-a050-f76568476411 /media/WD_2TB  ext3  defaults 0 2

---

### Post by meazz1 on 2010-11-30
bump

---

### Post by Wayne_V on 2010-11-30
I would recommend pmount:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

you can add this to your ~/.profile

---

### Post by meazz1 on 2010-11-30
> **Wayne_V said:**
> I would recommend pmount:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

you can add this to your ~/.profile

Thanks for the link.

---


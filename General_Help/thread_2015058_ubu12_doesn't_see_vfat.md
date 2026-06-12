---
title: "ubu12 doesn't see vfat"
date: 2012-07-02
forum: General Help
---

### Post by kaykav on 2012-07-02
Hi
      Since I reinstalled ubuntu 12.04 ,the system does not recognize 
               vfat , fat32, or fat16. Using my flash drive (usb),is 
                 not possible. It does not see vfat.   How can I resolve this problem?      Thank you...

---

### Post by cipherboy_loc on 2012-07-03
What do you mean by it cannot see vfat? Are you saying it cannot mount vfat partitions, or it does not find the partition, or it does not find the USB device? 

Post the output of:
```

sudo fdisk -l

```
This will list all current drives and partitions attached to the computer that Ubuntu sees.


Cipherboy

---


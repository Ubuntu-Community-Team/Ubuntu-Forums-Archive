---
title: "partitions"
date: 2009-08-10
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-10
are linux partitions not resizible? i am using gparted, but when i select my drive, i get no options, everything is greyed out and it shows the partitions locked.

reason is the end of my drive has bad sectors so i want to shrink the partions to get away from the bad area

---

### Post by michy99 on 2009-08-10
You can't change a partition while it is mounted. You need to boot from a Live CD and resize it from there.

---

### Post by AmerNewbieInDE on 2009-08-10
thanks

---

### Post by AmerNewbieInDE on 2009-08-11
well, i am in live cd, plugged in my external drive, dev sdc1 is still locked but dev sdc2 and 5 are not. i need to resize sdc1  so i can move 2 and 5.. anz ideas

---

### Post by zkriesse on 2009-08-11
I'll research it but it might take awhile...

---

### Post by AmerNewbieInDE on 2009-08-11
is it safe to unmount the drive, resize and move partitions, then remount.. and it will still boot? reason beiing, this is an external usb sata drive, i use it to run ubuntu.. it also has the boot loader

---


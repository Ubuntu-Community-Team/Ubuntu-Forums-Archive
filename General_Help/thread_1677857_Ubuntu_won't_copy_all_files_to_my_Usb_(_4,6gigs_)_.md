---
title: "Ubuntu won't copy all files to my Usb ( 4,6gigs ) Help!"
date: 2011-01-29
forum: General Help
---

### Post by chupize on 2011-01-29
Hello, 

so everytime i try to copy this file to my usb it just wont work it says '' too large file '' but that cannot be true the usb i am using have 30gigs free space left.
Its a .iso file that i am trying to copy it is 4,6gigs
( 4657807360 bytes )

---

### Post by JKyleOKC on 2011-01-29
If the USB device is formatted as VFAT, the largest single file it can store will be 4 GB no matter how much space is available. That limit is built into the file system.

To store larger files, the device must be formatted as NTFS. However reformatting it will erase all data already stored there so it's best done on a brand new drive.

---

### Post by chupize on 2011-01-29
ty that worked :-)!

---


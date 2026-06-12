---
title: "Error copying 7.3gb file to USB stick"
date: 2010-11-24
forum: General Help
---

### Post by Razmear on 2010-11-24
I am trying to copy a 7.3gb .iso file to an 8gb USB stick and I get the following error when it hits 4.0gb

Error while copying "xxxxxx.iso".
There was an error copying the file into /media/6262-FDBB.
Error splicing file: File too large

The file is to be used by a windows user, and I'm just trying to do a simple copy, not a burn to USB or anything fancy. 

Using 10.4.1.LTS, AMD Dual Core, all latest patches. 

Any ideas?
Thanks,
eb

---

### Post by Razmear on 2010-11-24
Discovered the USB stick is FAT32, which can't handle files larger than 4gb. Reformatting the drive.

eb

---

### Post by Razmear on 2010-11-24
Discovered the USB stick is FAT32, which can't handle files larger than 4gb. Reformatting the drive.

eb

---


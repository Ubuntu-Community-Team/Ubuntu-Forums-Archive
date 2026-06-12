---
title: "Removing wubi insatlled ubuntu and doing a fresh install"
date: 2011-06-23
forum: General Help
---

### Post by ubuntizer on 2011-06-23
Hello,

I have installed ubuntu within windows and now i want to remove windows forever.

How can i install ubuntu again and still preserve all my data which is in windows drive (which were getting mounted on wubi installed ubuntu)

Any help would be appreciated.
Thanks.

---

### Post by Beacon11 on 2011-06-23
I don't even need to reinstall Ubuntu; check this out: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

EDIT: I should have read a little more carefully, sorry. You have data in Windows, so you can't just wipe it like I was more or less recommending. Do you not have an external hard drive to use for temporary data storage while you install Ubuntu? If not, you can install Ubuntu in a smaller partition initially, mount Windows in the new Ubuntu install, move all the data over to where you want it, and then delete the Windows partition and resize Ubuntu's.

---

### Post by Frogs Hair on 2011-06-23
What data do you want to preserve the Ubuntu data , Windows data or both ? In either case you can save it to a removable device , but setting up a partition to access your Windows data is a bit more work . The Ubuntu data can be easily added from usb or cd to your new installation.

---

### Post by dandnsmith on 2011-06-23
Firstly, I think, you need to look at making space for separate partition into which you can move all the data (both from Windows and the embedded wubi install). You should be able to save the Ubuntu data as a suitable hierarchy to aid later manoeuvres, and the partition should be, preferably, ext3 or ext4, so you do the saves from Ubuntu.

HTH

---


---
title: "error mounting external HD? screenshot attached"
date: 2010-10-18
forum: General Help
---

### Post by princeofnam on 2010-10-18
here's the error message I recieve.  the HD had been working perfectly before until i transferred some files into it recently.

---

### Post by princeofnam on 2010-10-18
oops here

---

### Post by princeofnam on 2010-10-18
and also the HD works perfectly fine when I boot to windows.

---

### Post by JoelOl75 on 2010-10-19
Did you convert it from a basic to a dynamic NTFS partition?  That breaks things...

---

### Post by princeofnam on 2010-10-19
i'm not sure about the difference between the two, how one would convert it from one to the other, and how that would affect things.

i know i had originally wiped the HD to boot up to ubuntu and then formatted it to NTFS.  is that a problem?

---

### Post by JoelOl75 on 2010-10-20
No, sounds ok... You would convert a basic partition to dynamic in Windows by right clicking on the partition (In My Computer) and in the Properties change it to dynamic.  Or in Control Panel/Administration/Disk management

Note you don't want a dynamic partition but some options in Windows will convert it (Like spanning partitions and some otehr advanced stuff.

Did you try to backup all the data and reformat the disk?  Might be the last option.  Also, if it's removable be sure to eject it properly before unplugging it.

Sorry I couldn't be more help.

---

### Post by princeofnam on 2010-10-24
how would I fix this issue?  I tried to go to Disk Management, but I saw no option to convert back to Basic

---

### Post by JoelOl75 on 2010-10-25
So it is a dynamic partition?  The only way then would be to back up everything and reformat since you can't switch back.  Hopefully it's not the main C: boot partition, otherwise it's a windows reinstall. There's ways but not easy: 

[http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)

[http://technet.microsoft.com/en-us/library/cc757696(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc757696(WS.10).aspx)

A solution would be to create another ntfs partition (Or add another drive) and make a basic partition and share your data between Ubuntu and Windows on that.

I also heard of grub/boot problems with dynamic partitions but not sure if fixed:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/96115](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/96115)

---


---
title: "2nd Hard drive not detected"
date: 2006-03-11
forum: General Help
---

### Post by kittycatsexycat on 2006-03-11
I've just installed breezy after using dapper...

During setup i set up the partitions so that it wouldnt wipe the second drive but keep it reiser...

My mate said it would work better...

But now that i'm through the installation i cant find my second drive...????

Please can someone help me!!!!

:cry:

---

### Post by aysiu on 2006-03-11
Can you go to Applications > Accessories > Terminal and then post here the output of these two commands? ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by kittycatsexycat on 2006-03-12
i dont really know what that just did... but it didn't fix it if it was meant to...

i got it working last night...

but now without even touching anyhting its not working again...

---

### Post by taurus on 2006-03-12
If you want people to help you out, you need to supply what they've asked you for!!!  So, what's the output of those two commands from above again???

---

### Post by kittycatsexycat on 2006-03-12
Those two commands brings this up... i dont understand it....

kitty@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3556    28563538+  83  Linux
/dev/hda2            3557        3649      747022+   5  Extended
/dev/hda5            3557        3649      746991   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081   83  Linux

kitty@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by kittycatsexycat on 2006-03-12
Basically my hard drive is there but it is showing as empty...

i know for a fact that its not...

Its a 40Gb drive and its showing as having half free which is right...

---

### Post by kittycatsexycat on 2006-03-12
okay i worked it out... here's the solution...

Open disks in system...

Click on the 2nd drive, click partitions...

Check access path...

Mine wasn't set...

Dont forget to enable it...

Cheers to anyone who helped though   :KS

---


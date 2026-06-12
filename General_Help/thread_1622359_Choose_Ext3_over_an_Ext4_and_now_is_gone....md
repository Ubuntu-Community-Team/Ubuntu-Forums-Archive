---
title: "Choose Ext3 over an Ext4 and now is gone..."
date: 2010-11-15
forum: General Help
---

### Post by geneiros on 2010-11-15
Hi there...

i installed ubuntu 10.04 and accidentally choosen ext3 over my home partition ext4...and now it erased(?) all the files in my home folder...

is there a way to return the ext4 files???

please help...

---

### Post by Rubi1200 on 2010-11-15
Stop writing to the disk and use a LiveCD to boot the computer.

Download and install Testdisk from the repositories on the LiveCD:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Try and use it to recover the partition and/or files:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Hope this helps.

---

### Post by TBABill on 2010-11-15
Are you saying you have a separate partition for your home folder and when you installed 10.04 you installed the OS on that partition? And you formatted it to do the install?
 
If that's what you are saying I'm afraid you would have lost those files. I don't know any way to recover files when a disk was formatted, reinstalled with a different OS and using ext4 now instead of the older ext3. Maybe someone else will come along with more in depth knowledge of data recovery.

---

### Post by geneiros on 2010-11-15
Are you saying you have a separate partition for your home folder and when you installed 10.04 you installed the OS on that partition? And you formatted it to do the install?





no...

i have 3 partitions:

swap
/
/home

i installed ubuntu to / with ext4 format

but when choose the partition to be home i selected the /home partition but have choosen ext3 and the partition was ext4 but didnt choose to format and now everything is gone... in my home partition...


i'll try testdisk with livecd...



 
If that's what you are saying I'm afraid you would have lost those files. I don't know any way to recover files when a disk was formatted, reinstalled with a different OS and using ext4 now instead of the older ext3. Maybe someone else will come along with more in depth knowledge of data recovery.[/QUOTE]

---

### Post by geneiros on 2010-11-16
i used photorec and it recovered a lot of files....

but now the files have ramdom names...


one question...

does tune2fs can put back files in ext4?

it didnt format the partition just convert it to ext3...

---


---
title: "Change Disk portition and reload image file"
date: 2010-07-23
forum: General Help
---

### Post by moonhk on 2010-07-23
Hi All
My ubuntu partition is 19GB on 80GB hard disk. Then Reformat Hard Disk to 50GB and reload partimage image file. After reload the image file, using df to check Still 19GB. 

How to fix my problem ?

moonhk@hex:~$ df 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19061872   9667720   8433468  54% /
none                   1540188       328   1539860   1% /dev

---

### Post by Zeike on 2010-07-23
Can you be more specific as to how you created and 'reloaded' the image?

---

### Post by moonhk on 2010-07-25
Hi All

Step 1.
For Create partimage file by
YMD=`date +%Y%m%d`
TAR=/mnt/image/ubuntu104_${YMD}.gz
partimage -z1 -o -d save /dev/sda1 $TAR

Step 2.
Reformat HD 
About 50G for Linux, 30GB for NTFS

Step 3.
Reload /mnt/image/ubuntu104_${YMD}.gz to HD.

Found that by df -k, the size remain 19GB.

---

### Post by moonhk on 2010-07-30
For Partimage, I get the answer as below
[http://www.partimage.org/Partimage-FAQ#Can_I_restore_it_to_a_smaller_or_bigger_partition_.3F](http://www.partimage.org/Partimage-FAQ#Can_I_restore_it_to_a_smaller_or_bigger_partition_.3F)

You can't restore to a smaller partition (you will have an error), but it's possible to restore to a lager one. In this case, some space will be lost (I suppose the OS cannot use all the size). Partimage don't have a resize feature, but you can use other tools. I'd like to add this in the future too. It will allow to restore into a smaller or larger partition. Indeed, as Partimage is low level it uses data blocks. So resizing is possible, but that's a complex feature to implement. With some File Systems made to be easily resizable (as NTFS, ext2, ReiserFS), it may be easy, but with FAT, it's hard to do. For example, when resizing from 1,5 GB to 3 GB, you must change FAT16 into FAT32... You can use GNU Parted to do it.

---


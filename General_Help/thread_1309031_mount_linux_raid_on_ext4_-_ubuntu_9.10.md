---
title: "mount linux raid on ext4 - ubuntu 9.10"
date: 2009-11-01
forum: General Help
---

### Post by sammynl on 2009-11-01
Hi,
 
i'm a ubuntu geek and trying to learn. can someone please help me with the following question?
 
i'm running ubuntu server 9.10 and webmin 1.490
 
when i format the linux raid5 array /dev/md0 with filesystem ext4 (mkfs -t ext4 /dev/md0) and after that try to mount the array i get an error saying wrong fs. (i run the format command on the console and try to mount the array using webmin 1.490.)
 
then i format /dev/mdo with ext3 using mkfs -t ext3 /dev/md0 and **no** problem when mounting the array.
 
so, can a linux raid 5 array be formatted with ext4 or is it simply not possible:(? or is it a webmin bug hence i try to mount the ext4 array using webmin?
 
thanks in advance for any help or explanation.
 
sammy

---

### Post by sammynl on 2009-11-01
Solved, i found the solution or workaround :D:
 
After creating the linux raid array and formatting it with ext4, i did not try to mount the array using the "Linux Raid" menu option in Webmin > select RAID Device > "Mount RAID on:", but instead i went to System > Disk and Network File systems > Add Mount > New Linux Native Filesystem (ext4) > and selected RAID device.
 
[IMG]http://img5.imageshack.us/img5/593/raid0t.jpg[/IMG]
 
Result:
 
[IMG]http://img5.imageshack.us/img5/6218/raidsn.jpg[/IMG]
 
[IMG]http://img21.imageshack.us/img21/8553/raid2c.jpg[/IMG]
 
 
Yes, I still have a lot to learn about Ubuntu!

---


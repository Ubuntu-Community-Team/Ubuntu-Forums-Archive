---
title: "How to write to an hfs+ partition under Ubuntu"
date: 2010-05-24
forum: General Help
---

### Post by unckybob on 2010-05-24
I only have an ubuntu machine here, but I wish to transfer some files to her mac via my external hard drive. I only have an ubuntu machine here. 

I managed to make an hfs+ partition on my external hard drive using gparted after installing hfsprogs. I tried changing the permissions with chmod. The ls -l command yields: 

ls -l /dev/sdc1 
brwxrwxrwx 1 root disk 8, 33 2010-05-24 10:53 /dev/sdc1 

But I can't write anything to it. Can someone please help me?

---

### Post by unckybob on 2010-05-24
Figured it out. 

chmod a+rwx /media/[volumename]

---


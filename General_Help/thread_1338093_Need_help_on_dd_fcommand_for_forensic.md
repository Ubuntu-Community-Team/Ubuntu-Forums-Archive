---
title: "Need help on dd fcommand for forensic"
date: 2009-11-26
forum: General Help
---

### Post by Mystiques on 2009-11-26
Hi everybody i have tried to acquire an image of my VMware harddrive using the dd command but these are the results that i got
 
dd: writing to /media/sdb2/disk.dd : file too large
dd:writing to "standard output" : broken pipe 
 
Source VMware specifications=6GB
Destination device external hard drive=9.77
 
External hard drive file system FAT32
 
Source device file  system NTFS
 
Then i thought the reason for the failure was i didnt split the image, but i dont want to split the image i want to acquire it fully
 
I have tried to change my destination file system NTFS thinking that, it might work.But then i had  an error that the destination is "read only"
 
Im confused right now and i dont know what to do.

---

### Post by XCan on 2009-11-26
You'll have to change it to something that's not FAT32 supporting files > 4GB, for example, NTFS. The reason you get "read only" is probably because of incorrect ownerships when mounting it. When mounted, what does ```
 ls -l /media/ 
``` show? And how do you mount it?

---


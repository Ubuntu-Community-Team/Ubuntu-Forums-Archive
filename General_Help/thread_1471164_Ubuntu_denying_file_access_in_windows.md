---
title: "Ubuntu denying file access in windows"
date: 2010-05-03
forum: General Help
---

### Post by Gilded on 2010-05-03
Hi, i use dual boot with win 7 and ubuntu 10.04, i installed Win7 first on one partition, and afterwards Ubuntu 10.04 on a second partition on the same drive. Now when i try to delete some files in windows like old games that where on a other harddrive it sais 

"You require permission from S-1-5-21-293015479-4145159318-3171105019-500 to make changes to this folder"

How do i resolve the problem that ubuntu takes ownership over some folder/files?

I'm pretty new to ubuntu/linux so a simple answere is appreciated.

---

### Post by Gilded on 2010-05-04
I formated both partitions and reinstalled win 7 but the linux ownerships are still on the folders/files anyone knows where it all is saved?

---

### Post by Smart Viking on 2010-05-04
Write in terminal "gksudo nautilus" it will open the file browser as super-user, see if you get access then. :)

EDIT: Do not close the terminal until you are finished with nautilus, or else nautilus will close.

---

### Post by Gilded on 2010-05-04
I tried that and tried to change permission to let all users read and write, but when i right click on the folders and try to change permission it just wouldnt change, im copieng all files from that drive atm and will format the entire drive and make new partitions and hope it will work.
Something else i detected was that only the files on the same physical harddrive had their permissions changed. So i guess that ubuntu addat its permissions after win 7 and thats why i cant change it really.

---


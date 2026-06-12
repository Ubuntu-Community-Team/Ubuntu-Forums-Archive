---
title: "Cannot Boot into Vista (Was previously a dual boot with ubuntu Lucid)"
date: 2010-12-26
forum: General Help
---

### Post by Andrewmay16 on 2010-12-26
Hello, I deleted 2 ubuntu partitions using Vista's manager, and expanded the unallocated space in to the Vista partition. when I restarted a screen came up saying 
error: no such partition
grub rescue>
Is there any way I can fix this ( by deleting grub, or something...)
any help would be appreciated
thanks
Andrew

---

### Post by davidmohammed on 2010-12-26
On the original Microsoft DVD in the "boot" folder there is a program called "bootsect.exe". 

run 
bootsect.exe /nt60 c: 
to restore the Vista bootloader. 

(copy and paste from [here]("http://www.pronetworks.org/forums/how-to-restore-vista-boot-loader-t76643.html"))

---

### Post by Andrewmay16 on 2010-12-26
the computer only came with a recovery partition, not a disk.

---

### Post by davidmohammed on 2010-12-26
google brought [this one]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") up - hope it works for you.

---


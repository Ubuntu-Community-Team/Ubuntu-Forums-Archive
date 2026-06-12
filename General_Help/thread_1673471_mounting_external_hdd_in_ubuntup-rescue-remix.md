---
title: "mounting external hdd in ubuntup-rescue-remix"
date: 2011-01-22
forum: General Help
---

### Post by uk_dhacker on 2011-01-22
Issue mounting my usb external hdd in ubuntu-rescue-remix... 
i am trying to use photorec and recover the files to my external hdd but i m not able to mount my external hdd..

please help...

---

### Post by mikewhatever on 2011-01-22
Photorec should work on an unmounted file system. In fact, if you want to recover some files, mounting the file system is the last thing to do.

---

### Post by efflandt on 2011-01-22
I just downloaded the 10.10 rescue remix to check it out.  If it is a USB drive, what does **mount** show you after connecting it?  Mine showed that it automounted the 2 partitions on my drive as /media/usb0 and /media/usb1.

So maybe the partition(s) on your external drive already mounted and you just didn't know where to find them.  Try **ls /media/usb0** (zero).

PS: The OP is not trying to recover the external drive, but is trying to save anything recovered to the external drive.

---


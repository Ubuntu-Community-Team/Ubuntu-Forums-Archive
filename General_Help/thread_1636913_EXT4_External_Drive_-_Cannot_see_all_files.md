---
title: "EXT4 External Drive - Cannot see all files"
date: 2010-12-03
forum: General Help
---

### Post by CC801340 on 2010-12-03
I have an external USB drive formatted to EXT4. 
 
I can browse all folders without a problem. However, I can only see files under (I'm guessing this value) 400mb. Where a folder contains file(s) over that size, I cannot see the larger files. I am able to see smaller files in the same folder (eg jpgs).
 
Looking at the properties of the drive, it says 584GB used. However, the "Contents" are only shown as 89GB and then a message saying "some contents unreadable".
 
Is anyone able to assist so I can see ALL my files?
 
Many thanks

---

### Post by dcstar on 2010-12-04
> **CC801340 said:**
> I have an external USB drive formatted to EXT4. 
 
I can browse all folders without a problem. However, I can only see files under (I'm guessing this value) 400mb. Where a folder contains file(s) over that size, I cannot see the larger files. I am able to see smaller files in the same folder (eg jpgs).
 
Looking at the properties of the drive, it says 584GB used. However, the "Contents" are only shown as 89GB and then a message saying "some contents unreadable".
 
Is anyone able to assist so I can see ALL my files?
 
Many thanks

Use the Disk Utility to do a "Check Filesystem" on it.

---

### Post by CC801340 on 2010-12-05
Thanks for your reply.
 
I get the error "The device is busy" when I try and check the filesystem.
 
The partition I am trying to check is /dev/sdb3. Is there anything else I can do to check the filesystem?
 
I would guess that the filesystem is fine as I could see the data without any problems when the drive was in my QNAP NAS.
 
It also seems strange that it's only the LARGER files that I cannot see. I can see everything else.

---

### Post by CC801340 on 2010-12-12
Just for anyone else who is having this problem. 
 
I managed to fix this problem by downloading the QNAP Live CD and booting into this - [http://forum.qnap.com/viewtopic.php?f=144&t=11860](http://forum.qnap.com/viewtopic.php?f=144&t=11860)
 
Data saved!

---


---
title: "Ext4 sd card mounts as read-only"
date: 2009-08-02
forum: General Help
---

### Post by jeremy on 2009-08-02
I have a 2GB SD card, formatted to ext4 (have tried ext2 and ext3 as well, but it does not change the behaviour) and whatever I do, it is mounted as read only for user, root can write to it.

I have tried both hot plugging, and using fstab to mount it, it does the same either way. Curiously, if I format it to FAT32 it mount as rw for all users.

Any help on this matter would be greatly appreciated.

---

### Post by Tek-E on 2009-08-02
I am definatley no expert. but have you tried using the chown command to change the ownership of the device??

---

### Post by jeremy on 2009-08-02
Yes, I have tried chown to no avail. Thanks anyway.

---

### Post by ridetheteapot on 2009-08-02
'ls -l' where it is mounted, whats it say?
'mount' whats that say?
maybe through in a "ls -ln" and "id -u username" for good measure and double check.


hey did you turn journaling off for the card? i dont think you should use a journaling fs with a compactflash card. maybe should keep it fat anyway ? ;) or ext2.

---

### Post by jeremy on 2009-08-02
Thanks, I have already double checked all that, and tried ext2, same problem. I don't want to use FAT as it loses file permissions.

---


---
title: "boot mapping ?"
date: 2012-09-10
forum: General Help
---

### Post by Fotja on 2012-09-10
First to explain my hard drive before installing Ubuntu. Has 4 partition. The first is the system partition (/). The second partition is the swap. Third partition is a home (/home). Fourth partition is the backup. The intention was that after installing Ubuntu transfer backup manually, folder by folder, selectively to the /home partition.
During install I mount backup partition like the system folder (/a), hoping that it will be easier to move the backup to the /home partition. totally unnecessary!
I had a small problem with the ownership of the backup files but it all ended up as I imagined.
After moving my backup I could wipe the fourth partition.
I started computer with live CD (Parted Magic), erased the fourth partition and resize third to now unallocated part of the hard disk. Still raning live CD and went in the file system and delete /a folder (linked to the more nonexistent fourth partition).
My problem now is that when I start the computer during the boot I got a message:
"The disk drive for /a is not ready yet or not present. Continue to wait or press S to skip mounting or M for manual recovery"
To correct this I believe that it is necessary to edit the boot mapping ... but I do not know anything about it.
I do not want to make mistakes while playing with the boot mapping.
Thank you in advance for any assistance and I apologize for my bad English.

---

### Post by mcduck on 2012-09-10
All you need to do is to edit the /etc/fstab file, and remove the line where the now non-existent fourth partition is configured. If you want to play it really safe, you can also simply comment the line out (by adding a # in the beginning) instead of deleting it.

---

### Post by Fotja on 2012-09-10
Thank you McDuck.
I opened it in gedit but how to bypass "You do not have the permissions to save file..." ?

update:  I change the ownership of file, edit and attempted to save but now message is "Could not create a backup file while saving /etc/fstab ;  gedit could not back up the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?"
I hit "save anyway" but didn't save.

---

### Post by mcduck on 2012-09-10
Open a terminal, and run "gksudo gedit /etc/fstab" to open the file for editing with root permissions.

...and you might want to read this document about root account & use of sudo command in Ubuntu for admin tasks:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Fotja on 2012-09-10
Fixed it. 
Tx mcduck

---


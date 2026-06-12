---
title: "how to write to another partition? permission?"
date: 2006-02-06
forum: General Help
---

### Post by Choad on 2006-02-06
how do i become the owner of, or alternatively change the group of hda3. its a random fat 32 partition i use to store music etc, shared between xp and ubuntu.

shouldnt be too hard, but still i cant do it :(

---

### Post by cotcot on 2006-02-06
Make a directory /media/windows and add a line in /etc/fstab (sudo gedit /etc/fstab) supposing hda1 is the drive you want to get permissions on :

 /dev/hda1    /media/windows vfat  iocharset=utf8,umask=000  0    0

---

### Post by aysiu on 2006-02-06
Go to Applications > Accessories > Terminal and copy and paste these commands: ```
sudo umount /media/hda3
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace this line ```
/dev/hda3 /media/hda3 vfat defaults 0 0
``` with this line ```
/dev/hda3 /media/hda3 vfat iocharset=utf8,umask=000 0 0
``` Save. ```
sudo mount -a
``` This assumes, of course, that is was /media/hda3. If it's /media/windows, adjust appropriately.

---

### Post by Choad on 2006-02-06
cheers!

---

### Post by lha on 2006-02-06
With
```
/dev/hda3 /media/hda3 vfat uid=Choad,gid=SomeGroup,dmask=027,fmask=137,utf8 0 0
``` in your fstab, all files on hda3 will have Choad as their owner, giving him r/w access to all files. Members of SomeGroup are allowed to read all files. Other users aren't allowed neither read or write to files. (Executable bit is turned off on all regular files because we don't want Ubuntu to think those files are programs.)

---


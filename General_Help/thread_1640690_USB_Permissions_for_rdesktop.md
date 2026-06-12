---
title: "USB Permissions for rdesktop"
date: 2010-12-08
forum: General Help
---

### Post by Anessen on 2010-12-08
Hello,

I am currently trying to redirect USB drives as they appear in the /media folder to a remote Windows Server 2008 session. It works perfectly with folders that have full permissions for everybody (777). However 700, like on the USB stick, give a permissions error when trying to read or write to the drive inside the windows session. I can't change the permissions of the USB stick itself.

Is there a way to make the drive accessible to "everybody" or is there something else that I am missing?

EDIT:
The file system on the drive is FAT.

---

### Post by Anessen on 2010-12-08
Mounting the drive with:

sudo mount -t vfat -o umask=0,uid=nobody /dev/sdc1 /home/myuser/mydrive

works perfectly, is there a way of telling the auto-mount to do this? It's not much use if I have to do that every time I add a drive.

---

### Post by Anessen on 2010-12-08
The furthest I've got is editing the source of udisks as described in this thread:
[http://art.ubuntuforums.org/showthread.php?t=1606193](http://art.ubuntuforums.org/showthread.php?t=1606193)

I tried adding setting the umask to 000 in the vfat_allow options and it didn't do anything... 

Really at a loss now, we have about 90 of these little netbooks that need to be able to access the USB drive from an RDP session.

---

### Post by Anessen on 2010-12-09
So there is no way to force the permissions on this device?

---


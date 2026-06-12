---
title: "backup to external drive has problems because mount point changes"
date: 2010-06-02
forum: General Help
---

### Post by semick on 2010-06-02
I am backing up my filesystem with simple backup, and also my mysql server to a Western Digital usb hard drive.  The problem I'm running into is the original mount point starts out as /media/WD_External.  Then at some point, the drive must be unavailable or disconnected momentarily or something, because the backups run and actually create that directory instead of going to the external drive.  So then Ubuntu automounts it to /media/WD_External_.  So now the backups are going to a folder on the internal hard drive instead of the intended location.  Somehow this happens a third time and I now have the drive mounted on /media/WD_External__.  I don't have the drive in /etc/fstab, I don't know if that would help. 

Any Ideas on how I should do this properly?

---


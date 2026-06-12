---
title: "USB drive permissions"
date: 2006-02-21
forum: General Help
---

### Post by matthinckley on 2006-02-21
Hello everyone

Why is it everything on my USB disk is permission 700?

Me and my wife both use the disk and when one of us puts files from it into our shared folder on the computer, the other can't even access the file because of the 700 permission..

I've tried the fstab entry.. but because it's usb it doesn't always mount as the same device.. i.e. sometimes it is /dev/sdb1 and sometimes it is /dev/sdc1

Is there a way that I can change the default permissions for a vfat usb drive?

I've also tried changing the permissions in /etc/udev/permissions.rules by adding MODE="0660" to the scsi devices section, but it had no effect

I cant format it ext3 because the key also gets used in windows machines

Thanks

Matt

---

### Post by matthinckley on 2006-02-22
is there no solution to this?  This is the first problem I've had with Ubuntu that I haven't been able to find the answer to.. I'm sure there has to be some simple fix for this that I'm just overlooking..

---

### Post by Wide on 2006-04-19
Having the same issue here

---

### Post by axelb on 2006-04-19
[http://ubuntuforums.org/showthread.php?t=50242&highlight=mount+usb+pen+drive+share](http://ubuntuforums.org/showthread.php?t=50242&highlight=mount+usb+pen+drive+share)
gives a «quick an dirty» answer to this problem :-)

Mvh Axel Bojer

---


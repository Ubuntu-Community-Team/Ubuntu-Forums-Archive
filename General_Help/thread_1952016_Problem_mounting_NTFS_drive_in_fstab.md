---
title: "Problem mounting NTFS drive in fstab"
date: 2012-04-03
forum: General Help
---

### Post by mercury80 on 2012-04-03
Hi
I have a server running Ubuntu 11.04. It has several drives, most of which are NTFS. When I try to mount these drives from fstab I always get an error message during boot: "Serious errors were found while checking the disk drive for /media/MyFolder" and I get the choices to ignore, skip or manual recovery.

If I mount the drive with:
```
sudo mount -t ntfs-3g /dev/sdd1 /media/MyFolder
``` or ```
sudo mount -t ntfs-3g UUID=###### /media/MyFolder
```
It all works just fine! But if I try any of the of the following in my fstab I get the same errors during boot:
```

UUID=###### /media/MyFolder ntfs-3g rw,auto,user,fmask=0111,dmask=0000   0 1
UUID=###### /media/MyFolder ntfs-3g defaults,user,locale=nb_NO.utf8   0 1
UUID=###### /media/MyFolder ntfs-3g defaults   0 1
```


Any ideas?

---

### Post by jerome1232 on 2012-04-03
```
UUID=###### /media/MyFolder ntfs-3g rw,auto,user,fmask=0111,dmask=0000   0 [COLOR="Red"]0[/COLOR]
UUID=###### /media/MyFolder ntfs-3g defaults,user,locale=nb_NO.utf8   0 [COLOR="Red"]0[/COLOR]
UUID=###### /media/MyFolder ntfs-3g defaults   0 [COLOR="Red"]0[/COLOR]
```

Don't set ntfs disks to be checked, in fact, if it's possible, don't use ntfs. Go with a native linux format, I can't think of any reason to use ntfs on a server.

---

### Post by mercury80 on 2012-04-03
> **jerome1232 said:**
> Don't set ntfs disks to be checked, in fact, if it's possible, don't use ntfs. Go with a native linux format, I can't think of any reason to use ntfs on a server.

Sweet. That did the trick for the most of the disks! Tnx... (Setting the last digit in each line to 0, that avoids the check).

I still get an error on one of the disks: "An error occurred while mounting..." Gonna need some more research to resolve the error of that one...

I agree! I wish it was all ext4, but it used to be a Windows 2008 R2 server...

---

### Post by oldfred on 2012-04-03
Because Linux cannot do the file check for NTFS on every 40 or 60 reboots, you get no file checks. 

But Windows NTFS still should have chkdsk run, but you have to use Windows to run those file chkdsk.

 If Linux cannot mount it then it may be saying you have to run a chkdsk from your Windows repairCD.

---


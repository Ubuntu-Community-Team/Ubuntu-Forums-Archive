---
title: "trying to save files"
date: 2011-10-15
forum: General Help
---

### Post by gonewriting on 2011-10-15
So I recently upgraded to Oneiric Ocelot and had the terrible problem of no longer being able to boot.  After trying many different repairs I feel that I've messed things up even more and only want to completely reinstall everything.  The only problem is that I have an odt file I would like to transfer to an ipod for safekeeping until everything is back up and running again.  I have tried copying the file, but I receive the not-so-surprising error message of "Permission denied."
I am trying to move the file from a live CD of Oneiric Ocelot.  I do have a Windows HDD on this computer as well running MacDrive, if that makes any difference.  
Please let me know if there are any solutions. Thanks.

---

### Post by gonewriting on 2011-10-16
bump

---

### Post by AlphaLexman on 2011-10-16
You probably need root privileges, use sudo:
```
sudo cp /path/to/filename.odt /media/usbdrive
```

---

### Post by gonewriting on 2011-10-16
thanks! worked perfectly!

---


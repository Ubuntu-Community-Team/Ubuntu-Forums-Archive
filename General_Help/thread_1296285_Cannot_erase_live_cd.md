---
title: "Cannot erase live cd"
date: 2009-10-20
forum: General Help
---

### Post by M4rotku on 2009-10-20
Hey guys,

I have run into this problem many a times.  I make a live cd on one of my rewritable dvd's and then when I want to erase the disk to make a new or updated live cd, I am not allowed to erase the files.  Every time I have to boot up into Windows b/c it clumsily (but usefully) ignores all of the Unix permissions.  Is there any program or command for linux that I can use to override the permissions?

Much thanks,
M4rotku

---

### Post by Giblet5 on 2009-10-20
Are you running from the booted LiveCD that you're trying to erase?

That won't work very well...it's kind of a "Ubuntu needs Ubuntu to erase Ubuntu but if we erase Ubuntu then there will be no Ubuntu to erase Ubuntu."

You could cause space-time to warp.


You can erase any ISO filesystem (on RW media) that can be unmounted.

---

### Post by M4rotku on 2009-10-20
I am not running from the live cd.  In this case, I want to update my sysresccd, so I downloaded the new .iso, but I can't wipe the original disk.

---

### Post by Giblet5 on 2009-10-20
> **M4rotku said:**
> I am not running from the live cd.  In this case, I want to update my sysresccd, so I downloaded the new .iso, but I can't wipe the original disk.

If you can unmount it and it's rewritable, then you can erase it.

Try unmounting it first.

---

### Post by philinux on 2009-10-20
> **M4rotku said:**
> I am not running from the live cd.  In this case, I want to update my sysresccd, so I downloaded the new .iso, but I can't wipe the original disk.

You don't normally wipe these dvd rws as it shortens life for a start, just overwrite with something else.

---

### Post by M4rotku on 2009-10-20
How do I erase it if it is unmounted?

The only way I know of erasing stuff is to mount it and then use the file browser or cl to erase the files in the folder.

---

### Post by petersohn on 2009-10-20
Open up a CD burning program (Brasero on GNOME and K3b on KDE) and select the Erase CD option. Simply deleting the files won't work.

---

### Post by Giblet5 on 2009-10-20
> **petersohn said:**
> Open up a CD burning program (Brasero on GNOME and K3b on KDE) and select the Erase CD option. Simply deleting the files won't work.

+1

(I assumed. Again.)

---

### Post by M4rotku on 2009-10-20
Thanks guys

---


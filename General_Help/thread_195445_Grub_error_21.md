---
title: "Grub error 21"
date: 2006-06-12
forum: General Help
---

### Post by souteneur3190 on 2006-06-12
I have 2 harddrives.  One has ubuntu dapper and the other one breezy,  Of course breezy was installed first, but didnt work when i tried to update dapper.  so i made a fresh install on hardirve B and when I took the first one away b wont even start.  It seams like grub is installed on my first hardrive and not my second hardrive and even when i put it back i get grub error 21

---

### Post by pyromithrandir on 2006-06-12
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 
That's what error 21 is. Make sure you're putting the drive back in the way it was in before, as in Primary Master, Primary Slave, and so on for the Secondary drive too.

If that doesn't fix it, boot a livecd and reinstall grub.

---


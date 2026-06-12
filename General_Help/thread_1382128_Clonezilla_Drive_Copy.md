---
title: "Clonezilla Drive Copy"
date: 2010-01-15
forum: General Help
---

### Post by tom.swartz07 on 2010-01-15
Hi all,

I recently got a new replacement drive for my failing one under warranty. 320gb Western Digital Scorpio Blue. 

When I boot in LiveCD using clonezilla, I attempt to copy the drive as usual, but just before it copies, the process fails.
I assured that it was the same drive, the filesystem is intact on my source drive, and the new drive seems fine.

What's happening? 

Is there another way to copy my entire drive and the bootloader?

I know that theres the command if dd blahblahblah, but I dont know how to use it in this case.

---

### Post by Techsnap on 2010-01-15
Do you get any error messages?

---

### Post by tom.swartz07 on 2010-01-15
> **Techsnap said:**
> Do you get any error messages?

The only error message said that the program failed.
I assumed that it was because the target drive had no filesystem on it, but it only allowed the program to go just as far before failing again.

Im completely stumped, and im running out of cd's haha.

---

### Post by tom.swartz07 on 2010-01-15
If its any help, I checked the md5sum of the .iso before i burned it.


Can anyone verify if the command line method works?

What I mean to say, will```
dd if=/dev/sda of=/dev/sdb
```

Copy EVERYTHING, including the MBR (Grub)?

Normally, I would just say "heck with it" and just re-install Ubuntu, but theres an install of Windows 7 on this drive that I CANNOT lose.

Im really in a pickle, and pressed for time as the drive being replaced must be returned ASAP

---

### Post by tom.swartz07 on 2010-01-15
bump

---

### Post by Techsnap on 2010-01-15
Yep, that should work, remember you will loose anything /dev/sdb if you do that.

---

### Post by tom.swartz07 on 2010-01-15
I keep getting the error 

```
error: invalid partition table on /dev/sdb --wrong signature 0
```

what does that mean? 

Sdb is my external that I am backing up to

---

### Post by akakingess on 2010-01-15
If it is currently empty as a backup drive, then I would just unmount it and run gparted and try to create it again, maybe something is messed up with the filesystem, so creating a new partition and formatting it will hopefully fix it.

EDIT:  I just noticed that you were booting off of a LiveCD so the unmounting shouldn't be necessary, but you may have to install gparted before being able to use it.

---


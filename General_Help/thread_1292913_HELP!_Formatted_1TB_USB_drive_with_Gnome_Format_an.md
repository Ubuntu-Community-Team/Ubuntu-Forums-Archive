---
title: "HELP! Formatted 1TB USB drive with Gnome Format and now I can't do anything with it!"
date: 2009-10-16
forum: General Help
---

### Post by oldrocker99 on 2009-10-16
I just bought a Seagate 1TB external drive and intended to format it to ext2 so I could copy over my /home directory, which has some files which are >4GB. My first mistake was using Gnome Format instead of fdisk, I suppose, but, upon finishing, the drive couldn't be mounted and is now invisible. 

I tried "fdisk /sde1" and got

mount: can't find /dev/sde1 in /etc/fstab or /etc/mtab

and, sure enough, nothing there.

If I try Gnome Format again, I get 

/dev/sde: unrecognized disk label

In other words, I am stuck. Anyone who can help, let me know!

:guitar:

---

### Post by dandnsmith on 2009-10-16
You'd have to do *fdisk /dev/sde*, or get a drive list with *fdisk -l* to find out what drives can be 'seen', and then invoke fdisk.

HTH

---

### Post by lavinog on 2009-10-16
You can't assume the drive will be /dev/sde either...it could be /dev/sdf the next time you connect.

use ```
**sudo** fdisk -l
```

---

### Post by CharlesA on 2009-10-16
I'd just hook it up and run gparted to partition and format the drive.

---

### Post by beastrace91 on 2009-10-16
> **CharlesA said:**
> I'd just hook it up and run gparted to partition and format the drive.

Seconded. And also I'd recommend formatting the drive to ext3 (or ext4) as they are journaling file systems.

~Jeff

---

### Post by bhishan on 2009-10-16
Use gparted. I had a friend who had the same problem (he had formatted it to ext3, why are you using ext2 anyways), gparted worked for him.

---

### Post by lavinog on 2009-10-16
> **bhishan said:**
> Use gparted. I had a friend who had the same problem (he had formatted it to ext3, why are you using ext2 anyways), gparted worked for him.

Maybe he doesn't need the extra IO operations associated with using a journal.

---

### Post by oldrocker99 on 2009-10-17
I heard on another thread to try GPartEd, and I'll try that. Thanks.

:guitar:

---

### Post by lavinog on 2009-10-17
> **CharlesA said:**
> I'd just hook it up and run gparted to partition and format the drive.
this thread maybe?

---


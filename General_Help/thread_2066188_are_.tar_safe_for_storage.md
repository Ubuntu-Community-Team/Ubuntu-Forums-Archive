---
title: "are .tar safe for storage?"
date: 2012-10-04
forum: General Help
---

### Post by PGScooter on 2012-10-04
I would like to archive say, 1000 files of about a megabyte each. If one of the files gets corrupted, it's not that bad of a loss and I can still use the other 999. Should I store them unpackaged? Or should I put them in a .tar? I'm worried than if I put them in a .tar and a few bytes get corrupted then it is more likely that I can't recover some of the files.

I have seen many recovery tools, but I never know if I can trust them and I imagine they only work sometimes.

Am I correct in thinking that .tar is a safer choice than .tar.gz in the sense that if a few bytes are off in a .tar.gz it would be harder to recover some files?

---

### Post by stefangr1 on 2012-10-04
It would be safer and more efficient to use gzip or bzip2, and then use par2 to create a parity file that you can use to recover the lost data if parts of the file have been corrupted.

On the other hand, if the data is so important: why not make a backup and keep it in two separate places? Many if not most of the problems that cause data loss will result in a complete loss of data rather than just corrupting a few blocks of data.

---

### Post by Stonecold1995 on 2012-10-04
> **stefangr1 said:**
> It would be safer and more efficient to use gzip or bzip2

What?  I thought it's harder to recover a corrupt file when it's compressed...  I've had more trouble with recovering corrupt .tar.gz files than .tar files in my experience.

---

### Post by stefangr1 on 2012-10-06
> **Stonecold1995 said:**
> What?  I thought it's harder to recover a corrupt file when it's compressed...  I've had more trouble with recovering corrupt .tar.gz files than .tar files in my experience.

The compressing part was for efficiency, not for safety. On the other hand, if compressing results in - say - a 2/3rd reduction in size, it would be less space consuming to keep a few backups (on different disks).

The safety part was in the second part of the sentence you quoted: if you want a simple way to recover data if a few data blocks have been corrupted, you can use par2. Let's say your 1000MB of data is 300MB after compression. If you now create 100MB of parities, you can recover your data if - randomly - less than 1/3rd of all data blocks is gone.

---

### Post by Scott Harrison on 2012-10-06
IMO, It's more important to keep multiple backups, less chance of permanently losing anything that way.

---


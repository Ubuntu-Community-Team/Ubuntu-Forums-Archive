---
title: "moving files from ubuntu to vista"
date: 2009-08-07
forum: General Help
---

### Post by RastaManPower on 2009-08-07
hello guys is it possible to move files from ubuntu partition to vista partition whjile running on vista os?

---

### Post by yeeeev on 2009-08-07
The short answer: usually, no. The long one is: Depends on the file system in question. It can work if your "ubuntu files" are stored on an NTFS partition.
Normally vista can't read Ubuntu's file system (ext3, reiserFS, xfs, etc).
On the other hand, Ubuntu can read NTFS, so you can boot up ubuntu and copy files to the NTFS partition.

---

### Post by howefield on 2009-08-07
> **RastaManPower said:**
> hello guys is it possible to move files from ubuntu partition to vista partition whjile running on vista os?

Yes it is.

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

---

### Post by KinaU on 2009-08-07
Why don't you use an external hard drive, and transfer your files to it via USB, and when you have Vista, just plug in the ext. drive and transfer the files back. I'm very simple, but I know this will work. Hope I helped! :D

---


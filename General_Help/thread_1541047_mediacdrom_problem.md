---
title: "/media/cdrom problem"
date: 2010-07-28
forum: General Help
---

### Post by ctult on 2010-07-28
Hi!  I have a problem with /media/cdrom.  It thinks it is a folder.  I can't copy anything to the cd.  I have been searching for the past hour for info.  Can someone please help?

CTuLT

EDIT: I can provide more info.

---

### Post by AlphaLexman on 2010-07-28
ggggggggggg

---

### Post by AlphaLexman on 2010-07-28
Oops sorry 'bout that! Kittehs!

/media/cdrom IS a folder. It is a mount point for your physical device. ALL mount points must be mounted to an empty directory.

Even if you insert a CD-RW disc into a drive/device that will 'write' you cannot just "cp filename.ext /media/cdrom" with out the hardware abstraction layer daemon (hald) involved.

Programs like Brasero and k3b can handle this layer instinctively.

---


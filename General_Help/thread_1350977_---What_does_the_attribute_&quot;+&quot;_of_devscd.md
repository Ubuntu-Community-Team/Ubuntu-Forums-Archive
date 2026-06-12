---
title: "---What does the attribute &quot;+&quot; of /dev/scd0  mean"
date: 2009-12-09
forum: General Help
---

### Post by bzhao on 2009-12-09
when I copy (using cp -a command) a ubuntu 9.04 to another disk partition. I see the below warning:
cp: preserving permissions for `/mnt/tmp/dev/scd0': Operation not supported

and  then I ls that file and see like the below line:
brw-rw----+ 1 root cdrom 11, 0 2009-12-10 16:57 /dev/sr0

cp: preserving permissions for `/mnt/tmp/dev/scd0': Operation not supported

I feel the atrribue of "+" cannot be saved as a copy

Sombody know that?
how to set it and unset.

Bill Z

---

### Post by john newbuntu on 2009-12-09
You need to use the dd command to copy partitions or perhaps use an imaging/cloning software like clonezilla.  cp is for copying files and directories.  The + indicates that it is using Access Control Lists which gives it greater control of permissions.  I think the tune2fs command is used to set or modify it.  I must confess that I have not used it myself.

---

### Post by bzhao on 2009-12-09
> **john newbuntu said:**
> You need to use the dd command to copy partitions or perhaps use an imaging/cloning software like clonezilla.  cp is for copying files and directories.  The + indicates that it is using Access Control Lists which gives it greater control of permissions.  I think the tune2fs command is used to set or modify it.  I must confess that I have not used it myself.

really thank for your respone.
Traditionally unix people alway do this to bake up system. current I only found only this file have this attribue reported as a error.

---


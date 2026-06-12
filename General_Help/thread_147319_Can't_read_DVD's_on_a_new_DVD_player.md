---
title: "Can't read DVD's on a new DVD player"
date: 2006-03-20
forum: General Help
---

### Post by TriggerHappyChewie on 2006-03-20
I had an install of Ubuntu 5.10 with a CD burner that worked.  I just replaced that CD burner with a DVD burner/reader/CD burner/reader/.  But now when I put in a DVD, it mounts it under /media/cdrom, but nothing shows up.  Is there a way I can get linux to scan for "New hardware"?  I don't want to have to re-install...

---

### Post by Blunts on 2006-03-20
Example

 * To mount CD/DVD-ROM 

sudo mount /media/cdrom0/ -o unhide

    * To unmount CD/DVD-ROM 

sudo umount /media/cdrom0/

---

### Post by TriggerHappyChewie on 2006-03-20
Thanks!

---


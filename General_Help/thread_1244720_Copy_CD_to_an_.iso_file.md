---
title: "Copy CD to an .iso file"
date: 2009-08-19
forum: General Help
---

### Post by bilijoe on 2009-08-19
Is there a way to copy a CD [image] to an .iso file, or otherwise create an .iso image file from a CD?  I installed BlindWrite--don't know if that would do it or not, but can't find out as I can't find it in any menu or anywhere else. :confused: What I want to do is start with a DATA CD and create an .iso file from it.

---

### Post by Locutus_of_Borg on 2009-08-19
dd if=/mnt/cdrom of=~/cd.iso

after having first mounted the cd to /mnt/cdrom

---

### Post by vinnywright on 2009-08-19
K3b or I think brasero will make an .ISO from a cd/DVD as part of the coppy prosess

VINNY

---

### Post by pizmooz on 2009-08-19
I think you should take vinnywright's advice.

But just to clear something up, if you did it this way:
> **Locutus_of_Borg said:**
> dd if=/mnt/cdrom of=~/cd.iso
after having first mounted the cd to /mnt/cdrom
you want do have the cdrom device **unmounted** and then do
```
dd if=/dev/cdrom of=~/cd.iso
```
that is because you want to capture the block level information.

---

### Post by matthewbpt on 2009-08-19
Simplest way: put the cd or dvd in, right click the new disc icon on the desktop, click copy disk, and in new window that comes up under "select a disc to which to write" select image file and click properties to choose name and where to save it. Couldn't be easier!

---

### Post by bilijoe on 2009-08-20
Thanks guys. Brasero did the trick. I just hadn't looked through all its features.:popcorn::popcorn::popcorn::popcorn:

---


---
title: "Windows not unmounting Ubuntu drive correctly"
date: 2009-07-24
forum: General Help
---

### Post by jackhynes on 2009-07-24
Probably not the right place for this but whenever I access my ext3 Ubuntu drive using Windows Vista Ubuntu scans the drive (with no option to quit the scan) and tells me the drive has not been unmounted properly. Not sure whether I'm using the FS driver or ext2fsd.

How do I make Vista unmount properly?

---

### Post by sdlynx on 2009-07-24
Do you mean when you access your Ubuntu drive from Windows it gives you an error when you try to unmount it? I'm not sure if you can unmount drives on Windows that easily to begin with.  However, have you tried IFS drives?

---

### Post by jackhynes on 2009-07-31
> **sdlynx said:**
> Do you mean when you access your Ubuntu drive from Windows it gives you an error when you try to unmount it? I'm not sure if you can unmount drives on Windows that easily to begin with.  However, have you tried IFS drives?

If I have accessed my Ubuntu partition in Windows at all (even if only opening My Computer and the partition being accessed to show its available space) and then restart and boot back into Ubuntu during the disc checks it says the drive hasn't been unmounted properly. Being a ~300GB drive this takes a long time! I suppose this isn't a Ubuntu issue, more of a Windows one but does anyone know why Windows isn't unmounting the Ubuntu partition cleanly?

**Edit:** I think I am using ext3 IFS drives to access the partition from Windows.

---

### Post by jackhynes on 2009-08-04
bump

---

### Post by jackhynes on 2009-08-08
one more bump

---

### Post by jackhynes on 2009-08-13
last bump

---

### Post by Greenwidth on 2009-08-13
Windows doesn't unmount properly in my experience.

A Google search found this:
[http://serverfault.com/questions/11350/is-it-possible-to-mount-unmount-a-physical-hard-drive-in-windows-xp](http://serverfault.com/questions/11350/is-it-possible-to-mount-unmount-a-physical-hard-drive-in-windows-xp)

Which may or may not be helpful..

---

### Post by fennec_fox on 2009-08-13
> **jackhynes said:**
> Probably not the right place for this but whenever I access my ext3 Ubuntu drive using Windows Vista Ubuntu scans the drive (with no option to quit the scan) and tells me the drive has not been unmounted properly. Not sure whether I'm using the FS driver or ext2fsd.

How do I make Vista unmount properly?

I have had this problem with USB drives and external hard drives. The only way I can ever get them to unmount properly is if I actually use the safely remove tool from windows to remove it and even then it fails sometimes. If it's a partition or another hard drive does it show up in the safely remove menu on vista?

---

### Post by jackhynes on 2009-08-13
> **Greenwidth said:**
> Windows doesn't unmount properly in my experience.

A Google search found this:
[http://serverfault.com/questions/11350/is-it-possible-to-mount-unmount-a-physical-hard-drive-in-windows-xp](http://serverfault.com/questions/11350/is-it-possible-to-mount-unmount-a-physical-hard-drive-in-windows-xp)

Which may or may not be helpful..

Have you tried either method?

---

### Post by jackhynes on 2009-08-13
> **fennec_fox said:**
> If it's a partition or another hard drive does it show up in the safely remove menu on vista?

It's a partition, and they don't show up in the Safely Remove Hardware thingy. Don't think there is a right click > Unmount option either.

---


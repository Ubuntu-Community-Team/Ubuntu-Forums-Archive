---
title: "Flash drive problems"
date: 2009-07-19
forum: General Help
---

### Post by BslBryan on 2009-07-19
Hello all. :-)

I've got an 8 GB flash drive that I'd filled up, so I deleted everything.  For some reason, it shows free space being just over 800 MB.  

FTR, yes, I've emptied root's trash, too.  

To better explain everything, I've provided a screenshot.  Does anyone have any ideas?

---

### Post by utnubuuser on 2009-07-19
this thread related maybe?> [http://ubuntuforums.org/showthread.php?t=867335]("http://ubuntuforums.org/showthread.php?t=867335")

or is this a bootable drive?

If this a bootable usb drive, check this thread:> [http://ubuntuforums.org/showthread.php?t=974398]("http://ubuntuforums.org/showthread.php?t=974398")

---

### Post by BslBryan on 2009-07-19
Hey utnubuuser. :-)

Thanks for the quick reply, but it's not quite the kind of thread I've been looking for, though the concepts are similar.  Anyone else have an idea?

---

### Post by BslBryan on 2009-07-19
Didn't see the edit, sorry.  :P

In the second thread you linked to, it mentioned something along the lines of a "trash can for the flash drive."  

I can't seem to find any documentation on this that refers to anything other than the trash on my desktop, which I've already emptied.

---

### Post by BslBryan on 2009-07-19
SOLVED!

I ran ```
sudo dosfsck -rV /dev/sdb1
``` which recognized that my flash drive was reporting an incorrect number of available space and corrected the problem.

---


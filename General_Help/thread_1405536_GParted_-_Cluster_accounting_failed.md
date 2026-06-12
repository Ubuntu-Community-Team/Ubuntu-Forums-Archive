---
title: "GParted - Cluster accounting failed"
date: 2010-02-12
forum: General Help
---

### Post by 3DCGdesign on 2010-02-12
I've looked all over the web, but don't see an answer to my particular case...

I'm in GParted in Ubuntu Live CD 9.10 amdx64

To prep for Ubuntu install, I'm attempting to resize and re-partition my second hard drive which was *FORMERLY* my primary boot drive for Vista before it crashed a few days back.  It is *CURRENTLY* my Vista User data file and is about 250Gb in size.  The drive is a SATA 500Gb total.  

But GParted now all of a sudden gives me **several "Cluster accounting failed at *blah blah*: missing cluster in $Bitmap**" error messages.
[COLOR=Red]
_Is there a good way to 'fix' these errors?_[/COLOR]  (besides reformatting it)


***I deleted the long-winded background, so let me know if you need more info.***
Short version:
I installed vista by reformatting my 120Gb data drive as the primary master now.
Then I plugged in my 'previous' 500Gb Sata drive, and pointed Window's User folder to my old User folder, and voila, was back up and running in Vista... minus all my programs... 

but now, both drives are recognized by GParted as "boot" drives.

All my respect/thanks in advance to you!  I've read/learned a lot here the past few days.

---

### Post by lavinog on 2010-02-12
> **3DCGdesign said:**
> 
But GParted now all of a sudden gives me **several "Cluster accounting failed at *blah blah*: missing cluster in $Bitmap**" error messages.
[COLOR=Red]
_Is there a good way to 'fix' these errors?_[/COLOR]  (besides reformatting it)


Find a windows machine, plug your drive into it, and do a disk check.

---

### Post by 3DCGdesign on 2010-02-13
he he... exactly what I did while waiting for a reply.

worked like a charm.  ;)  Thanks!

---

### Post by forsubhi on 2012-02-23
I don't have windows now , is there is another solve

---

### Post by dcstar on 2012-02-25
> **forsubhi said:**
> I don't have windows now , is there is another solve

If you don't have Windows then you don't need to use useless NTFS partitions, do you?

---


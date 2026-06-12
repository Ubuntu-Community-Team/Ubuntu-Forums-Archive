---
title: "HDD Copy tool"
date: 2010-01-17
forum: General Help
---

### Post by RedSingularity on 2010-01-17
Hey everyone.  Here is the deal.  I need to copy the contents of one drive to another new drive.  I mean EVERYTHING on it including the OS itself.  I am thinking Clonezilla at the moment.  Any other suggestions?  

Thanks.

---

### Post by alwayshere on 2010-01-17
Clonezilla will do it

---

### Post by frenchn00b on 2010-01-17
> **RedSingularity said:**
> Hey everyone.  Here is the deal.  I need to copy the contents of one drive to another new drive.  I mean EVERYTHING on it including the OS itself.  I am thinking Clonezilla at the moment.  Any other suggestions?  

Thanks.

dd with tar.gz   backup 
or clonezilla 

check here
[http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm](http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm)

amanda is used for backup through networks

---

### Post by spcwingo on 2010-01-17
Ghost4Linux...I've used it with 100% success rate so far.  :)  Here's a link to their SourceForge page:

[http://sourceforge.net/projects/g4l/]("http://sourceforge.net/projects/g4l/")

---

### Post by RedSingularity on 2010-01-17
Ghost 4 Linux looks interesting.  Is it a bootable CD?

---

### Post by spcwingo on 2010-01-17
> **RedSingularity said:**
> Ghost 4 Linux looks interesting.  Is it a bootable CD?

Yes it is.

---

### Post by RedSingularity on 2010-01-17
Just curious, Why is it called "ghost 4 linux" if it can clone HDD's with windows as well?

---

### Post by spcwingo on 2010-01-17
I have have no idea...that's something for the devs to answer.  ;)

---

### Post by Cheesemill on 2010-01-17
Just fire up a Live CD and use dd. To copy sda to sdb just do:
```
dd if=sda of=sdb bs=1M
```Make sure you get the drive letters correct or you'll copy an empty drive onto all your data!!

This will only work if the destination drive is the same size or bigger than the source drive.

---

### Post by Cheesemill on 2010-01-17
Or you can use Gparted on the Live CD.

---


---
title: "Renaming photos in KDE4"
date: 2010-09-14
forum: General Help
---

### Post by XtremeGamer99 on 2010-09-14
Hello,

I'm trying to batch rename 3,300 photos, and can't figure it out.

I've tried digiKam and KRename, however I can't figure out how to simply rename the files as such:

~/Pictures/[year]/[month]/[datetime].JPG

where the year, month, and datetime are when the picture was taken, via EXIF data. In digiKam, I can't figure out how to rename the files to move to a different dirrectory than their current one, and with KRename, I can't figure out how to only use the year for the directory instead of the entire datetime.

Are there any easy solution for this? It seems really simple...

---

### Post by quixote on 2010-09-15
Conceptually simple, advanced vector analysis for a computer.  What you really need is a shell script to do that, and I've never been able to write a renaming one that works, so you don't want my advice on that.

What's your starting point?  That is: do you already have that dir structure, year/month/ ?  Are you just trying to rename IMG0053.JPG (or whatever) to $datetime.JPG?  Or are you trying to create those directories at the same time?

---

### Post by dreikin on 2010-09-26
Try this: [https://help.ubuntu.com/community/Photos/BatchRenaming](https://help.ubuntu.com/community/Photos/BatchRenaming)

---


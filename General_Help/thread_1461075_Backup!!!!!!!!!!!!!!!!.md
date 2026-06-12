---
title: "Backup!!!!!!!!!!!!!!!!"
date: 2010-04-23
forum: General Help
---

### Post by sudoer541 on 2010-04-23
its time to backup my data, cuz lucid is coming out!!!!!!!!!
Here is what I want to accomplish...I want to install lucid and customize it. 
Later, I want to backup my hard drive (Drive Imaging) What software can I use to backup my partition? 
OOOOHHH!!!!! and how can I apply the image I took? 
Can I just use the live CD, install the backup program (insert name here) and click on import? 

In simple words: 

Backup hard drive (drive imaging)> save to DVD or external HDD > use live CD to apply the image I took > restart the PC and everything to normal.

Is that possible???

---

### Post by beercz on 2010-04-23
[http://ubuntuforums.org/showthread.php?t=1460579](http://ubuntuforums.org/showthread.php?t=1460579)

---

### Post by Ric_NYC on 2010-04-23
Again?


:)

---

### Post by sudoer541 on 2010-04-23
> **beercz said:**
> [http://ubuntuforums.org/showthread.php?t=1460579](http://ubuntuforums.org/showthread.php?t=1460579)


but that thread does not answer my question. I want to backup my partition (create an image of my partition) then I want to know how to restore my OS back through the live CD. 

Any ideaz?

---

### Post by ajgreeny on 2010-04-23
If you have a separate /home partition just either copy it to a USB hard disk, or use rsync to do that for you.

If you really do want or need a clone of the whole disk take a look at clonezilla.  THis will not need a separate ubuntu live CD as it works that way itself.

---

### Post by swoll1980 on 2010-04-23
Use clonezilla it's great. Just google for a tutorial.

---

### Post by The Real Dave on 2010-04-23
+1 for Clonezilla. It utterly rocks. My backups would be so much more tedious without it :)

---

### Post by K.Mandla on 2010-04-23
+1 for Clonezilla. It's only the bestest thing ever.

---

### Post by beercz on 2010-04-24
> **sudoer541 said:**
> but that thread does not answer my question. I want to backup my partition (create an image of my partition) then I want to know how to restore my OS back through the live CD. 

Any ideaz?

There are loads of threads on this in the forums.

Boot to a live CD, mount your harddisk and use rsync to back up your harddisk to an external drive or network pc or whatever you are backing up to.

For regular backups I use [rsnapshot]("http://rsnapshot.org").

---


---
title: "simple samba question?"
date: 2009-12-21
forum: General Help
---

### Post by titanicmusic14 on 2009-12-21
I have two hard drives. I have one set up as my Samba share. I would like to add another hard drive to that same share. how is that done? meaning two hard drives one share in one main folder  then 1 folder 1st hard drive, and 2nd for the other. or something like that.

---

### Post by Fire_Chief on 2009-12-21
You could mount the drives as subfolders of a root folder instead of in root itself. i.e.
/smbshares/drive1mount
/smbshares/drive2mount

Then you configure Samba to share /smbshares itself.

Cheers!

---


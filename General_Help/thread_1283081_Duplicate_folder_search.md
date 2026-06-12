---
title: "Duplicate folder search"
date: 2009-10-05
forum: General Help
---

### Post by ksadil on 2009-10-05
Hi,

I want to be able to process my archive hard disk, and find whole folders that are duplicates. I know fdupes and gqview do a great job of individual files, but I am sure I have whole folders duplicated on my archive hard disk.

If I have to write an app I am thinking of using python to:
(1) make a list of all of the folder names in the drive.
(2) where the folder names are the same check the filecount & folder size is the same, 
(3)then do a checksum on each file. and report the duplicates folders.

Any alternatives or suggestions would be greatly appreciated. Also any feedback on if this would be useful for you would be interesting as well.

Thanks,
Kim

---

### Post by ermeyers on 2009-10-05
Learn some basic unix and shell commands.
man find
man diff
man cmp
man `basename $SHELL`

(1) make a list of all of the folder names in the drive.
find path -type d

diff -qs path1 path2
diff -qs path1 path2 | grep -v identical

cmp -s file1 file2
if [ $? = 0 ];then echo same; else echo different; fi

---

### Post by ksadil on 2009-10-05
just found this:

[http://code.activestate.com/recipes/362459/](http://code.activestate.com/recipes/362459/)

---

### Post by StuartN on 2009-10-05
> **ksadil said:**
> just found this:

[http://code.activestate.com/recipes/362459/](http://code.activestate.com/recipes/362459/)

fdupes is stable and mature, in the repositories

---

### Post by jarble on 2012-09-01
> **StuartN said:**
> fdupes is stable and mature, in the repositories

Does fdupes make it possible to find duplicate folders (not just duplicate files)?

---

### Post by Kangarooo on 2012-10-26
Im also looking for that. I dont need duplicate files to find. They are too many. I need percentage or number of similarity orderable by size.

---


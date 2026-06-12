---
title: "error copying file to external drive."
date: 2010-08-02
forum: General Help
---

### Post by orky7 on 2010-08-02
i have this .mkv file of a movie which is of size 7.9GB and when i try to copy it to my external drive after some time it shows a error saying "Error splicing file: file too long" so how to copy help

my external HD's file format is vfat. and i am using ubuntu 10.04

---

### Post by howefield on 2010-08-02
I think you are limited to a file size of 2 gigabyte on that.

---

### Post by orky7 on 2010-08-02
so how to increase it? or any other method

---

### Post by orky7 on 2010-08-02
it get stuck when it reaches 4GB mark

---

### Post by orky7 on 2010-08-03
as i already said that my external HD is vfat and so it is going to support max file size of 4GB-1byte, so i have to convert the vfat drive to ntfs and you can convert vfat to ntfs without formating the drive go to command prompt(windows) and 
type >convert *drive_letter*: /fs:ntfs
it will convert if there is no error in the drive if any error in the drive run 
> chkdsk /f driveletter

i do not know if there is any application to convert vfat to ntfs without formating in linux. there may be...

---


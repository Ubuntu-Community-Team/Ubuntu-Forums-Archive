---
title: "Permission denied"
date: 2012-07-22
forum: General Help
---

### Post by manjaba on 2012-07-22
I want to write c programs with Geany to a memory stick. After the program is saved to the stick, it compiles ok but I get a permission denied when I try to run it. I have tried to right click on the file and go to permission properties and check the box marked "execute" but it does not stay checked.

I'm not sure how to use the command line to go to the file on the memory stick and try a chmod.

---

### Post by ironic.demise on 2012-07-22
try this:
```
 chmod 777 'path/to/file' 
``` Obviously remove the qoutes and put in the full path to the file, for example chmod 777 /media/stick/file

777 is read/write/execute for everybody so you might want to try the longer version of rwxr--r-- which is read write execute for the owner, but only read for groups and other users.

by the way, the first number is for the owner of the file, the second number is for groups the file is linked to and the third number is for others which is, well, others.

7 is RWX and the breakdown for the number is 1 is execute, 2 is write and 4 is read... you just add the ones you want together.

(if I remember correctly)

---

### Post by efflandt on 2012-07-22
What file system is on the memory stick?  If it is the usual FAT32, that has no concept of file permissions, but can be set with mount options **umask** or **fmask**.  Although FAT32 is typically **vfat** to Linux, those options are listed under **fat** in **man mount**.  Although, I am not sure how to get that to apply when something like a USB memory stick auto mounts.

---

### Post by ironic.demise on 2012-07-22
Just had a thought, is the stick write protected, I know he put files on there but some sticks the write protect can be a physical switch which may have changed?

and some sticks I have used have become corrupted, but the only difference is that nothing can write, but everything can read.
Maybe try the stick in windows?

---

### Post by manjaba on 2012-07-22
Thanks Ironic et al.

The stick (HP v100w) is FAT 32 and I was able to run the program with DevC on Windows XP.

In a terminal I typed:

bill@bill-UL80VT:/media/HP v100w$ chmod 777 helloGeany.c

and got:

./geany_run_script.sh: 5: ./geany_run_script.sh: ./helloGeany: Permission denied

---


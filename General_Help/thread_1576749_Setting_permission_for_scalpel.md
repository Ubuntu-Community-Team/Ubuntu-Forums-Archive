---
title: "Setting permission for scalpel"
date: 2010-09-17
forum: General Help
---

### Post by mattofsmeg on 2010-09-17
I have been trying to recover data off an external hard drive using scalpel.  I got the files types done set up the external folder and then I go to run the program and I get an error message "ERROR: Couldn't open input file: /dev/sdb -- Permission denied"  I tried resetting the permission for the external by right clicking the drive and going through the permission menu but every time the permission reset themselves.  Got any advice.

---

### Post by e79 on 2010-09-17
> tried resetting the permission for the external by right clicking the  drive and going through the permission menu but every time the  permission reset themselves.  Got any advice.

You can either try to insert a line in your **/etc/fstab** as shown in this post :

[http://ubuntuforums.org/showthread.php?t=916884](http://ubuntuforums.org/showthread.php?t=916884)

or try this one suggesting to do a **fsck** **-r** to check the disk consistency for errors as suggested here :

[http://ubuntuforums.org/showthread.php?t=1066534](http://ubuntuforums.org/showthread.php?t=1066534)

Hope this helps

---

### Post by a.toraby on 2011-04-06
you can use sudo command

---


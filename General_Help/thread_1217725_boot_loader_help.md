---
title: "boot loader help"
date: 2009-07-19
forum: General Help
---

### Post by physic.dude on 2009-07-19
How can I remove OSs from the list.
 i.e. remove all but WinXP and Ubuntu kernel 2.6.28-13-generic.

I currently have 7 OSs on that list 

Ubuntu 9.04, kernel 2.6.28-13-generic 
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic 
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition
Windows NT/2000/XP

But I only installed 2 OSs
 IDK witches ones are important to leave on the list

---

### Post by c0mput3r_n3rD on 2009-07-19
I would touch the different Linux kernels, I'm sure what dependencies they have with each other.  How ever you have delete the other partitions that hold the operating systems that you don't want.   
```

sudo apt-get install partitionmanager

```And then proceed to use the partition manager to edit your partitions. 

***BECAREFUL! IF YOU DON'T KNOW WHAT PARTITION IS WHAT, DON'T TOUCH IT!!!! 
DON'T TOUCH A PARTITION LABELED AS "SWAP"***

EDIT: Go to add/remove programs and install a different a partition editor.
It will say KDE partition editor, and GNOME partition editor.  KDE partition editor should be selected, so; unselect th KDE partition editor, and select GNOME partition editor.  Sorry for the bad command. :\

---


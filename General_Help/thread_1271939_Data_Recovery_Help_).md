---
title: "Data Recovery Help :)"
date: 2009-09-21
forum: General Help
---

### Post by ephman on 2009-09-21
hi,

i accidentally loaded microsoft vista on a hard drive that what was an ubuntu 9.10 installation.  because i'm not that familiar with vista, i'm not sure it formatted the drive to ntfs.  i'm assuming it did.  any help would be great!  any gui recovery tools out that?

thanks,

ephman

---

### Post by jerrrys on 2009-09-21
this may work

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by cholericfun on 2009-09-21
if vista did install on your linux partition it had to partition it to ntfs cause it cannot use the ext formats.

IF you had anything on your Ubuntu partition:

DON'T move copy/install load anything onto that harddrive!!!
there are some tools that can try and recover data - beforehand DONT touch that partition!

theres a few threads around regarding recovery tools

good luck

---

### Post by ephman on 2009-09-21
i think i'm going to be out of luck.  i didn't realize it until i already upgraded the vista, and loaded about 80gig extra onto that drive.  the chances are really really slim there's that singe directory i need.   see another reason i haven't used any microsoft products for like 8 years now.  :(  oh well.  thanks for the help.

ephman

---

### Post by earthpigg on 2009-09-21
give testdisk and photorec a shot.

you will not be able to recover everything, but you may be able to recover some of it...

...it will be an ardous and time consuming project.

boot from an ubuntu livecd.

```
sudo apt-get update && sudo apt-get install testdisk
```

then try testdisk and photorec:

```
sudo photorec
sudo testdisk
```

do not have it save recovered data to that hard drive. find another one, and point testdisk and photorec there to save recovered files.

you will then need to dig through alllll that recovered stuff to find your files. they will probably have lost their file names, too... 

instead of mydocument.doc or img_001.jpg, it will be fea35a25a4c.doc and 3a3affac.jpg.

you will have thousands of them.

---

### Post by ephman on 2009-09-23
:( nothing left to recover.  didn't find anything.  oh well.  no worries it's only a computer.

ephman

---


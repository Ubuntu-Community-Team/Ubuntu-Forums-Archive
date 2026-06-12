---
title: "Help with terminal session"
date: 2010-02-15
forum: General Help
---

### Post by j22 on 2010-02-15
I have 3 main directores - C: a winxp drive, F: winxp to store backups, K: on which ubuntu 9.10, the swap file, and a NTFS data partition sits.  C: & F: are NTFS also.  I created a test folder on F: named 'test folder'.  In ubuntu with nautilus I can access this test folder, copy files into it, etc.   However, from a terminal session, when I try to change directory to this folder I get an error stating no such file or directory.  I tried cd using test_folder, testfolder, etc.  

What's the situation here?  I researched a couple of on-line linux sites but found no explaination.   Can someone please show me the proper way of naming the directory or accessing it in terminal?

Thanks !

---

### Post by lavinog on 2010-02-15
is the f: drive mounted?
if 'test folder' is located in the current folder:
```
cd "test folder"
or
cd test\ folder

```
you need to use quotes if there is a space in the name...this is the same as in windows command console.

---

### Post by lavinog on 2010-02-16
Is this a wubi install?

If you are having trouble mounting the "f:" drive:  You should be able to mount it simply by clicking on places, then the drive label. (Note: the use of drive letters is a windows thing...it dates back to the early days of DOS)
The normal location of mounted drives is in /media

```

cd /media
ls

```
should show some folders...one might be a bunch of random characters...this is likely to be the recently mounted drive (I am guessing that they use the random characters to ensure that two drives with the same label do not conflict.)

---

### Post by j22 on 2010-02-16
Yes F: was mounted.  Putting quotes on "test folder" did the trick.  Now I can proceed with script writing.

Thank you for the help!!

---


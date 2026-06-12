---
title: "Office file extensions"
date: 2010-08-22
forum: General Help
---

### Post by glowell on 2010-08-22
Hi,

I was wondering...I have Microsoft Office 2007 Enterprise edition installed through Wine on the latest Ubuntu Desktop edition. 

I am hoping to find a way where if I downloaded or created a word document, power point and so on to my desktop I can have them automatically open to the appropriate Microsoft Office application.

Any help would be greatly appreciated.

Thanks.

---

### Post by ajgreeny on 2010-08-22
Easy.

Just right click on one of the files (doc, docx, xls, whatever) ->**Properties ->Open With** tab and choose the application in that.  You will probably need to enter the wine full pathway for the executable to use, but it is so long since I used wine that I really can't remember.  I do know that it works, however, as I used to do it for a mass of Lotus Smartsuite Wordpro files which at that time could not be opened by OOo; luckily the few of those that I have left, and are now needed, can be opened in OOo without a problem now.

---

### Post by Trilby on 2010-09-27
I think your problem is the same as mine (see [http://ubuntuforums.org/showthread.php?t=1582428](http://ubuntuforums.org/showthread.php?t=1582428)).
MS Word (& etc) appears on the Open With list but this has the same effect as double clicking (see linked thread). I can't find the application in the .wine or .winetrickscache folders either.

---

### Post by Trilby on 2010-10-08
I've solved the problem using the "open with" command:
```
/usr/share/playonlinux/playonlinux --run "Microsoft Office Word 2007"
```
for Word

```
/usr/share/playonlinux/playonlinux --run "Microsoft Office PowerPoint 2007"
```
for PowerPoint

```
/usr/share/playonlinux/playonlinux --run "Microsoft Office Excel 2007"
```
for Excel

Note that this will only work if you installed through playonlinux.

---


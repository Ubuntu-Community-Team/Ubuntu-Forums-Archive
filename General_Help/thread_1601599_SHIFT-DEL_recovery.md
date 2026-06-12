---
title: "SHIFT-DEL recovery?"
date: 2010-10-20
forum: General Help
---

### Post by awambawamb on 2010-10-20
Hi people
the question is simple. I had a FAT external pendrive with some thing of it, and I've stupidly shift-del eted 2 folders that now i needed. Could be possible to retrieve the deleted files?

thanks!

Max

---

### Post by 3Miro on 2010-10-20
1. Stop using the pen drive immediately and absolutely do not write anytihng new on it.

2. Read very carefully:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by coldraven on 2010-10-20
Also try Photorec, it's in the repository, search for Testdisk. (You get two utilites, Testdisk is for partition recovery)
Photorec is primarily for images but finds other stuff too, Word docs for instance.
See here [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Running Photorec in a terminal will generate lots of directories, some contain bits of old overwritten files but some might have your prized files. I think you can specify what type of file you're after to get more precise results. I have used it successfully but not for a while.
Good luck :)

See here for file types: [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

---

### Post by awambawamb on 2010-10-28
hi there

sorry for answering so late, but i've had some problems that kept me away from internet and all those things...

as suggested, i've made an image of the partition on the device, and "scalpeled" the files from it.

magically, i found that some of the contents that i was searching for were there!

then also other files and sub-folders could be there: is there a way to recover them, even without their original names, but keeping the directory tree as it was?

thanks

---

### Post by MarkAlter on 2010-10-28
Hi awambawamb,

You can retrieve the deleted files from your pen drive with the help of Kernel for recover lost file software which will preview your lost data in scanning and if you want then you can recover them and save them to specific location. You can check the demo version of the software from - [http://www.recoverlostfile.org](http://www.recoverlostfile.org)

Thanks

---

### Post by awambawamb on 2010-11-12
hi guys

sorry, the problems has not been solved yet. so i'm trying to explain better my situation: 

I deleted a folder with SHIFT+DEL. (ok, that's a dumb move)

I realized it was the only copy i had, and immediately after deleting I've made an image of the volume and stored it safely on my machine.

I've used SCALPEL on the disk image and i found that some files that were in the deleted folder were present, along with many other. so, I realized, **my files must still be in that image**.

problem: i've seen how to recover the files. I need to recover their PLACES in the subdirectory tree. I mean: the deleted folder was called "tesi", inside this folder there were many folders: images, book, revisions, latex, ecc. I need to recover the structure of my deleted folder and the files inside it.

i hope to have been clearer, thanks for help.

---


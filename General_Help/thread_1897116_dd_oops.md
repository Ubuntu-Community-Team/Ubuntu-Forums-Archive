---
title: "dd oops"
date: 2011-12-18
forum: General Help
---

### Post by musashi39 on 2011-12-18
I accidently dd'd to the wrong drive now my hard drive shows up as a 3.8gig iso. Can I recover what wasn't written over?

---

### Post by WorMzy on 2011-12-18
You (probably) won't be able to recover *everything*, but might be able to recover some files using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and/or [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by sudodus on 2011-12-18
+1
I have experience from *PhotoRec*. You can recover several kinds of files from locations outside the overwritten part of the disk. But you have lost the file names and the directory structure. Some files contain the file name or something similar, for example the exif structure of jpeg files. Then some other tool can recover a meaningful file name. Open Document files are found among compressed archive files (I think zip) because they are such files.

---

### Post by Synoc on 2011-12-18
I generally when using dd specify an outfile to a file for example, backup.iso. on another drive, so I can't accidently wipe out a disk. it's very useful in the future. 

and if you want to make it easier still you can even write a script to have that drive backup to an file on the destination drive.

---

### Post by Habitual on 2011-12-18
It's not called Disk Destroyer for nothing.

---


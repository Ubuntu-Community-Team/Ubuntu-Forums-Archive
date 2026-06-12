---
title: "extract certain file from 7z / 7zip archive"
date: 2010-05-03
forum: General Help
---

### Post by maghajan on 2010-05-03
Hi, I have a 7zip archive and I would like to extract certain files from with it.  Is there a way to do this without un-compressing the entire archive?  I know these files exist in there because I am using the "7za l" command to view the files contained in the archive.  I have tried come google searches but no luck.  Any help is appreciated!

---

### Post by matthus on 2010-05-25
p7zip should work with archive manager fine, is in the synaptic, works well with ark also

---

### Post by mister_playboy on 2010-09-06
7z's default behavior is to create "solid" archives for better compression.  It is impossible to extract single files from such archives.

---

### Post by phylae on 2011-01-04
> **mister_playboy said:**
> It is impossible to extract single files from [solid] archives.

That is not accurate. I'm not claiming that the original poster's request is possible, but it is possible to extract a single file from a solid archive. Worst case scenario the program doing the extracting will extract every file, but delete it if it isn't the desired file. The process will take just as long as extracting all the files, but it won't use up the disk space.

---


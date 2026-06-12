---
title: "Zip archive has lost it's folder hierarchy?"
date: 2012-09-10
forum: General Help
---

### Post by jerome1232 on 2012-09-10
So I rescued files off of a computer, put it in an encrypted zip archive. The zip archive is 32 gb's. When I run a test on it, the contents are listed correctly in their subfolders, however if I actually extract it into a clean empty directory, eventually it prompts me asking if I want to overwrite a file which is already there, I opted to rename the files automatically and it proceeded to spew every.single.file on the top level directory, as well as every.single.folder on the top level directory, each folder is empty.

I'm at a complete loss as to what is going on here, is there a way to restore the folder hierarchy, I was in the process of converting this zip into a tar.bzip2 when I discovered this.


edit: as an example I ran this just now to test:

```
7z e Mom-backup.zip "Mom-backup/Documents and Settings/Bobbi Jones/My Documents/My Pictures/" -otest  
```

Which correctly extracted everything under that folder in the archive to the local directory test, however inside test I have the same situation where everything just got slathered all over the top level directory regardless of what the hierarchy should've been, folders, files, subfolders and all

---

### Post by jerome1232 on 2012-09-12
Ha! Turns out this was my own stupidity getting in my way, apparently the e option for 7z simply extracts each individual file, the x option extracts with the paths intact. The below successfully extracted the archive, it is now in tar.bz2 format.

```
7z x /path/to/archive.zip -odestination/directory/
```

:guitar:

---


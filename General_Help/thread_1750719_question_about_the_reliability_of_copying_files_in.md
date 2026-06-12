---
title: "question about the reliability of copying files in ubuntu"
date: 2011-05-05
forum: General Help
---

### Post by fuzzylogic25 on 2011-05-05
I have noticed something. If you copy/move a file (lets say 2GB in size) to another directory/drive, and quickly cancel it, it seems to still show in the destination directory, but with incomplete file size (maybe like 50MB). Then if you try to copy it again it asks for a replacing. that is okay, but if you are copying folders, where these files are present in, it asks for a merging. Now if you try copying destination to source (the reverse), merging will replace the 2GB file with the 50MB file.

This results in loss of data. Windows does not seem to do this. If you copy a file, and cancel it half way, the file will not show up at all (rather than showing up incomplete, which is what ubuntu does). This increases the reliability of merging in any direction (merge source in destination or vice versa).


My question is, why does ubuntu do this? And, is there anyway to stop it from leaving a file incomplete?

---

### Post by zvacet on 2011-05-06
I'm not an expert but 

> My question is, why does ubuntu do this?

I think because you told it so.You started action and after some some time canceled it.If action is not completed results will be incomplete.Why don't you in that case just remove files from destination directory?

---


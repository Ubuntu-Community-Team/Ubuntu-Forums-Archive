---
title: "Data Loss When Transferring Large Number of Files"
date: 2010-07-20
forum: General Help
---

### Post by treynorm89 on 2010-07-20
This problem is not exclusive to Ubuntu, I've experienced it in Windows and OSX as well, but it seems that almost every time I transfer a large number of files (i.e. my music collection) between my desktop computer and laptop via my external hard drive, I end up losing files for no reason. I usually don't notice the files are missing until later on, because I am never informed of any data loss. Does anyone know what might cause this?

Now, every time I make a large transfer of files, I just do it two or three times to ensure that I don't lose any files.

---

### Post by rubylaser on 2010-07-20
If you want to ensure consistent transfers for a large number of files, you could use rsync
rsync -avz /path/to/files/ /new/path/

To verify that everything worked once it's done, you could do another rsync after it's finished running.

---

### Post by ajgreeny on 2010-07-20
I wonder if you have files of the same name on your ubuntu box, but different case, ie some upper case, some lower case, which is fine on ubuntu, but not on windows file systems such as ntfs or fat32, which your external disk is likely to be.

I would expect an error message, however, asking "<filename> exists; do you want to cancel, skip or overwrite", so I may be wrong about that as a possible cause of your loss.

---


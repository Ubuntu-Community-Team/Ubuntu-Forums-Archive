---
title: "How to undo 'cat' command ?"
date: 2010-02-25
forum: General Help
---

### Post by MajinSaha on 2010-02-25
I typed command 
```
cat file_name1 file_name2 > file_name1
```
in order to combine two files and overwrite "file_name1" !
I know now, it was careless. The contents of "file_name1" just disappeared.
Is there anyway I can undo that command to restore my "file_name1" ? My terminal is still running. Since that point I only typed 2-3 commands.
Please help !

---

### Post by nimrodwebdesign on 2010-02-25
I think that's it, you've lost it. There's no undo in the commandline.

I learnt the hardway not to directly overwrite files as well. Either make a copy first, or output to a different file then replace the original when you are happy with the results.

Sorry, I can't be more help. I hope it wasn't a really important file.

---

### Post by lavinog on 2010-02-25
depending on what the two files contained, you may be able to recover most of the data the beginning of the file would have been overwritten with the second file, but the difference should still exist in an area on the filesystem marked as free space...assuming it was larger than one block (4k)
If you plan to recover the data, you need to not write anything to the drive, and unmount it (you should use a live cd)
It will take a long time to recover any part of the data, but photorec is a good program for recovering lost files.

---

### Post by spiderbatdad on 2010-02-25
might also still be in temp if the terminal hasn't been closed...
something like this: [http://www.finalcog.com/undelete-open-file-from-inode](http://www.finalcog.com/undelete-open-file-from-inode)

---

### Post by MajinSaha on 2010-02-25
Thanks for the comments guys.
It's ok, I realized I had an older version of the file. It only took me 10 minutes to add new things to make the same file(or similar) I lost.
I will remember these advices for future.

---


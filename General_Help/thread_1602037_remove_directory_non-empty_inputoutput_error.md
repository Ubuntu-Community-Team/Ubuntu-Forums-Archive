---
title: "remove directory non-empty input/output error"
date: 2010-10-20
forum: General Help
---

### Post by Ctulhu on 2010-10-20
I have a question that has been asked before but the answers don't work. I want to delete a folder that's not empty. Tricky things:

- it's the (hidden) .Trash folder on an external hard drive
- there seems to be a strange type of error.

So, I try rm -rf:

ctulhu@ctulhu-acer:~$ rm -rf '/media/1TB_Fantom/.Trash-1000'
rm: cannot remove `/media/1TB_Fantom/.Trash-1000/expunged/740528847': Directory not empty

But that directory IS empty, nothing in there (also nothing hidden):

ls -alR /media/1TB_Fantom/.Trash-1000

ctulhu@ctulhu-acer:~$ ls -alR /media/1TB_Fantom/.Trash-1000
/media/1TB_Fantom/.Trash-1000:
total 16
drwx------ 1 ctulhu ctulhu     0 2010-10-20 19:10 .
drwx------ 1 ctulhu ctulhu 16384 2010-10-17 09:06 ..
drwx------ 1 ctulhu ctulhu     0 2010-09-15 10:32 expunged

/media/1TB_Fantom/.Trash-1000/expunged:
total 20
drwx------ 1 ctulhu ctulhu     0 2010-09-15 10:32 .
drwx------ 1 ctulhu ctulhu     0 2010-10-20 19:10 ..
drwx------ 1 ctulhu ctulhu 20480 2010-07-09 11:07 740528847

/media/1TB_Fantom/.Trash-1000/expunged/740528847:
ls: reading directory /media/1TB_Fantom/.Trash-1000/expunged/740528847: Input/output error
total 0

"Input/output error" - what do I do to get rid of this folder??

Thx,
C

---

### Post by Pollox on 2010-10-21
Do you still get the same error if you prefix the rm command with "sudo"?

---

### Post by Ctulhu on 2010-10-21
Yes, I had tried that, too, to no avail.

---


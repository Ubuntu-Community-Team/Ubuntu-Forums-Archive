---
title: "Unable to delete file after cancelling unzip"
date: 2012-03-29
forum: General Help
---

### Post by mbroshi on 2012-03-29
For reasons unknown, I canceled an unzip midway with a ^c.  In that directory I see both foobar.zip and foobar.  Nonetheless, when I try "rm foobar", I get the error message 

rm: cannot remove `foobar': No such file or directory

or similarly 

rm: cannot remove `foobar.zip': No such file or directory

Similar commands get the same error message (mv foobar, sudo rm -i foobar, etc.).  In case it makes a difference, I dual boot in Oneiric and Windows, and these files are on my Windows partition. (I cannot delete them or rename them when booting into Windows either, where it tells me the files are corrupted.)

Any thoughts?

---

### Post by mbroshi on 2012-03-29
Solved my own problem.  Ran CHKDSK in Windows, which defragmented these files and they are now gone.  Still not exactly sure what the problem was, but all is well now.

---


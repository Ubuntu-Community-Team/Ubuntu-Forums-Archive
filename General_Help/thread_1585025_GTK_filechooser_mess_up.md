---
title: "GTK filechooser mess up"
date: 2010-09-29
forum: General Help
---

### Post by eexpress on 2010-09-29
so stranger things.. GTK file chooser **sometimes** return error filename.

eg:
$ ls
A.jpg B.pdf C.xml

when i use GTK file choose dialog, select C.xml. it return B.pdf. when B.pdf, i got A.jpg. 

seems file node reduce 1?

and in my perl script, use an filechooserbutton, i **always** got this trouble now.

2.6.32-25-generic, but seems not business with kernel. i always upgrade to newest 10.04.

---

### Post by lievenmoors on 2010-10-05
I'm having the same experience with dwm. Very strange indeed...

---

### Post by eexpress on 2010-10-09
so if you use reiserfs? 
my /home is reiserfs. filechooser normally operate on this partition.

---


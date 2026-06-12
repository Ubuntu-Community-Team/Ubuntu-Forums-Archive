---
title: "Forceful Removal Of Files/Folders"
date: 2011-11-10
forum: General Help
---

### Post by erbad on 2011-11-10
I am using the following command from a terminal session to delete files/folders:

rm -rf DIRNAME

The command has worked well, but now I'm left with three folders that have spaces in the directory names.  These three folders are:

Documents and Settings
Program Files
System Volume Information

When I try and delete these three folders using the above command, it doesn't work and I suspect it has to do with the spaces.  Would someone know how I can delete these three folders from a command prompt?

Thank you

---

### Post by carranty on 2011-11-10
You have to use the backslash character before the spaces

*rm -rf Documents\ and\ Settings*

should do it.

---

### Post by ajgreeny on 2011-11-10
Or you can put the filename (and full pathway, if using it) in quotation marks, eg, "file name"

---


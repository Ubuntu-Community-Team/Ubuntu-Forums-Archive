---
title: "gnome help printing broken"
date: 2010-03-26
forum: General Help
---

### Post by linuxcss on 2010-03-26
when I try to print a document from gnome-help (Help 2.28.0)
many times I get nearly a blank page printed,

and if I try to File->print this document it will just crash,
for example try printing the F-spot manual

I have tried this on multiple machines with same result

these machines are running Karmic

if I invoke gnome-help from a command line I see a Segmentation fault (see below);
anyone have suggestion how to fix this issue??

-------------------------------------


user1@cw1:~/test$ gnome-help

** (gnome-help:12284): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (gnome-help:12284): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.
OMF category 'Applications|Other' not recognised, ignoring.
I/O error : Is a directory
I/O error : Is a directory
Segmentation fault
user1@cw1:~/test$

---

### Post by bobcollard on 2010-03-26
Just looked at the f-spot user guide.  Since it is not PDF format you cannot open it all up for printing, you have to open each individual section.  You are only printing the table of contents, not the whole thing.  Nothing wrong with your computer or your printer, just the way you are trying to copy the information.

---


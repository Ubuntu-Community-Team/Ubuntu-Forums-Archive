---
title: "using file-manipulation tools"
date: 2010-04-23
forum: General Help
---

### Post by hungerformore on 2010-04-23
i need a good lesson in using file manipulation tools on the command line

---

### Post by kanikilu on 2010-04-23
It would probably help to know what you are trying to achieve...

If you want to append to a file, you can use a simple redirect. If you want to search a file, grep is your man. There's sed, awk, diff, and so on...it really depends on what you need to do.

---

### Post by quadproc on 2010-04-23
> **hungerformore said:**
> i need a good lesson in using file manipulation tools on the command line
Perhaps you are looking for an introduction to bash?  If so, a Google search will turn up a few things on the net.  Or there are several books on the subject.

Chances are that the tools to do what you need already exist as part of the standard installation.  These commans have manual entries that you can access by typing```
 man <toolname>
``` in a terminal window.  Most of them also have more extensive documentation available by typing ```
info <toolname>
``` into the terminal window.

Some of the tools are quite powerful.  For example, sed is a stream editor, awk is report generator, sort allows sorting of file contents by fields, and dd is a copying utility which is capable of doing anything to a file, even destroying the contents of a disk!

quadproc

---


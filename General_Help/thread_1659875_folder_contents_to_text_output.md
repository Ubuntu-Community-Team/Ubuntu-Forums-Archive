---
title: "folder contents to text output"
date: 2011-01-04
forum: General Help
---

### Post by dirtyHANS on 2011-01-04
again, i plead,pray, and hope - right click any folder, list contexts and subdirectories to text file-
and yes, i have tried ls,find, ect - need script for nautilus - PLEASE!!!!

---

### Post by lithopsian on 2011-01-04
The command you need is ls > file, but you will need to substitute something into the command to make it operate on what you want.  So it might be ls %d > file.  You will also probably want a way to specify the filename?  You could make it automatic based on the directory name or something like that, but it might be nicer to build in a prompt.

---

### Post by mikewhatever on 2011-01-04
Vague help requests frequently go unanswered here, so you might want to specify what's wrong with ls for listing files and folders. Just tried it, and **ls -R > file.txt** seems to work.

---


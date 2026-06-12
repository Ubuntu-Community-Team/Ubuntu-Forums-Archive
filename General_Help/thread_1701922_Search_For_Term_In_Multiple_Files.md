---
title: "Search For Term In Multiple Files"
date: 2011-03-07
forum: General Help
---

### Post by spikoley on 2011-03-07
I am trying to search for a term in a bunch of files.  Is there a way to do this.  I would like to search all the files in a directory and its subdirectories for a specific term.

---

### Post by veggen on 2011-03-07
grep is made for that ;)
Check out [this simple tutorial](http://blamcast.net/articles/recursive-grep-find-strings-files).

In short:
<grep -r "modules" .> to list matching lines
<grep -lr "modules" .> to list file names

---


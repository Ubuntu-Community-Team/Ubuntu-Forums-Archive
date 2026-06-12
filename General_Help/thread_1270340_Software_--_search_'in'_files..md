---
title: "Software -- search 'in' files."
date: 2009-09-19
forum: General Help
---

### Post by dE_logics on 2009-09-19
I needed a software to bulk search within files (pdf, odt, ods, djvu etc...) placed in the hardrive for strings.

For instance I wanna search "frequency polygon" and I give it a folder containing lots of documents to search for, and it returns me the results.

---

### Post by Keith Hedger on 2009-09-19
this ```
find . \! -iname '*~' -print |xargs grep -s --ignore-case --binary-files=without-match --line-number "frequency polygon"
```
will list all the files that contain the words "frequency polygon" and the line numbers where it apears in the current directory.
Just put this in a suitable script and bobs your uncle, if you havn't got much scripting experience indstall the abs-guide in the repos (Advanced Bash Scripting).

---

### Post by dE_logics on 2009-09-20
Ok, thanks...but this will search PDFs, ODT etc... right?

---

### Post by 3rdalbum on 2009-09-20
Try installing something like Beagle, Strigi or Pinot - they are disk content indexers.

---

### Post by dE_logics on 2009-09-20
disk content indexers?

---

### Post by Keith Hedger on 2009-09-20
> **dE_logics said:**
> Ok, thanks...but this will search PDFs, ODT etc... right?
Whoops! sorry not pdfs at least not if the strings are compressed in any way:(

---

### Post by mike555 on 2009-09-20
Beagle is excellent.

---

### Post by dE_logics on 2009-09-20
PDF is the main issue

Ok...I'll try beagle

---

### Post by kaibob on 2009-09-20
> **dE_logics said:**
> PDF is the main issue

Ok...I'll try beagle
I believe to search PDF's with a command line you have to use pdftotext, the output of which is then piped to a utility such as grep. If a GUI is available, that would be best.

---

### Post by dE_logics on 2009-09-20
I think beagle is pretty good, but I cant find a way to make it search into a specific folder...+ I do not want that indexing service.

---


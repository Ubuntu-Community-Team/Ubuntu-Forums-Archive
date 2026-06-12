---
title: "Error extracting file from zip"
date: 2010-10-09
forum: General Help
---

### Post by mediax on 2010-10-09
I'm trying to extract a file from a zipped archive, and receive an error message saying "caution: filename not matched:".

I suspect the route cause of this is that the original filename contained accented characters (which now show as question marks in the zipped filename).  I've tried renaming the file in the archive, but get the same error.

Any suggestions for getting the little blighter extracted successfully would be much appreciated!  I'm using 9.10 (Karmic).

Ian

---

### Post by lbrty on 2010-10-09
What is the full name of the file with the extension (e.g. ebook.tar.gz or ebook.zip, etc)?

---

### Post by mediax on 2010-10-09
The zip file is 

Old files.zip

and the problematic file it contains is

D?j? vu.doc

which should be Deja vu.doc, and which I suspect contained an accented e and a in the original title.

The error I get is:

caution: filename not matched:  D\?j\? vu.doc

---

### Post by minotavrs on 2010-12-14
> **mediax said:**
> The zip file is 

Old files.zip

and the problematic file it contains is

D?j? vu.doc

which should be Deja vu.doc, and which I suspect contained an accented e and a in the original title.

The error I get is:

caution: filename not matched:  D\?j\? vu.doc

Try this Fix..
Go to the directory containing the zip files and enter this command via terminal:

```
unzip \*.zip
```

enjoy...

---


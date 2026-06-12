---
title: "Problem with rar archive"
date: 2010-01-29
forum: General Help
---

### Post by Jompa on 2010-01-29
I have a problem unpacking a rar archive and wondered if there was anything I could do or if the file is just broken. I get an error (see attached picture)

---

### Post by gradinaruvasile on 2010-01-29
Install 7-zip:

sudo apt-get install p7zip

and in a terminal cd to the file and type:

7z l filename

Thats lowercase "L". And if it works, extract it with 

7z x filename

---

### Post by Jompa on 2010-01-29
That solved it, thank you! Also found out that there was some problems with the filename, but using tab made it spell it so that it accepted the filname.

---

### Post by jesterthejedi on 2010-02-04
It needs pzip-full to work.

---


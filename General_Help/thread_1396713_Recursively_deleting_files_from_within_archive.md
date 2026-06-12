---
title: "Recursively deleting files from within archive"
date: 2010-02-02
forum: General Help
---

### Post by Simbamangu on 2010-02-02
I've got a directory of geographic data with ~2,000 archives. Each archive (e.g. foo.zip) has two files, the second of which I'd like to remove:
foo.tif
foo_num.tif

Now, I can remove the _num.tif file with the command:
zip -d foo.zip \*_num.tif

How do I do this with ALL the files in the directory? If I try the -r (recursive) option, that fails with -d.

---

### Post by whiskeylover on 2010-02-02
```
#!/bin/bash
for ZIPFILE in $(ls *.zip); do 
    zip -d $ZIPFILE \*_num.tif; 
done
```Give this a try.

*backup your files to a different directory first, as I haven't tested this.

---

### Post by Simbamangu on 2010-02-02
That worked perfectly! Thanks very much.

Guess I need to learn more about scripting ... having ventured only into single commands so far.

---

### Post by whiskeylover on 2010-02-02
[http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial) <-- bash scripting tutorial for beginners :)

---

### Post by jamesisin on 2010-02-02
Please mark your thread as SOLVED in Thread Tools above.

---

